## Bat file folk use to inflate commits@echo off

:: Change directory to the specified Git repository

cd "C:\Github staging area\How-to-inflate-your-commits-"



:: Ensure the branch name is correct (replace master with your branch if needed)

SET BRANCH=master



:: Loop to continuously update the files, commit, and push

:loop

    :: Suppress LF to CRLF warnings for this repository

    git config core.autocrlf false



    :: Generate a random line of text and append it to the text file

    echo %RANDOM% >> file.txt



    :: Generate a random Python comment and append it to the Python file

    SET /A rand=%RANDOM% %% 5

    IF %rand%==0 SET COMMENT=# TODO: add error handling

    IF %rand%==1 SET COMMENT=# FIXME: improve performance

    IF %rand%==2 SET COMMENT=# HACK: temporary patch

    IF %rand%==3 SET COMMENT=# REVIEW: check logic flow

    IF %rand%==4 SET COMMENT=# NOTE: optimize later



    echo %COMMENT% >> "file.py"



    :: Stage both files

    git add file.txt

    git add file.py



    :: Commit the changes with a message including the current timestamp

    git commit -m "Update made at %date% %time%"



    :: Push the commit to the correct branch

    git push origin %BRANCH%



    :: Wait for 1 second before the next iteration

    timeout /t 1 >nul

goto loop
