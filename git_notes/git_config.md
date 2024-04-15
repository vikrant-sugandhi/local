
# Git Commands - Beginners hands on git status git clone git commit git push git log git add and more:

git clone <remote_url>
git log
git status
git log --patch -1
git log -p -1
git add .
git restore --staged <file>
git commit -m "message here"
git status
git branch -r
git branch -a

# one set of demo codes for refernce:
mkdir Moon
cd Moon
touch <filename>
vi <filename>
git add .
git commit -m "message here"
git remote add origin https://github.com/vikrant-sugandhi/test.git
git remote -v
git branch -M main
git push -u origin main


ls -a
rm -rf .git
git init


**=================================================================================**
1. **create directory:**
mkdir <dir_name>

2. **initiate repository with git:**
git init

3. **create files folders whatever you want**

4. **check git status:**
git status

5. **add files/dir to staging area:**
git add .
or 
git add <file1> <file3> <file3> ... <fileN>
e.g:
git add file1.txt file2.txt
git add *.txt

6. **how to commit:**

git commit -m "Initial commit."
# if discription is longer
git commit
*now editor opens and add a short description ideally less than 80 Char and close the editor window*
*then X for exit Y for save*

git status


commiting best practices:




# Skipping the staging area(git add .) command:
# Do if u know code is not required to be reviwed.
echo test >> file1.txt
git commit -a -m "Fix the bug that prevented user from signing up."
or
git commit -am "Fix the bug that prevented user from signing up."

**5.1 : if want to remove staged files i.e after (git add .) command:**
git restore --staged <fiename>

**5.2 : to completely remove / revert to time when cloned:**
git restore <file>

6. **commit:**
# here -m : message
git commit -m "Initial commit."
# if discription is longer
git commit and  enter 
now editor opens and add a short description ideally less than 80 Char and close the editor window
*then X for exit Y for save*

**=================================================================================**

7. **removing files from project:**
**7.1. remove from working dir**
**7.2. then from staging area** 
**7.3. commit changes**
#remove from working repo
rm file2.txt
git status
*to check files in staging area*
git ls-files
#remove from staging area:
git add file2.txt
git ls-files
git status
#remove from git repo
git commit -m "Remove unused code."

**To remove file at-once from both working repo and staging area: 1. remove from working dir and from staging area, 2. commit changes**
git rm file2.txt 
or 
git rm *.txt
git ls-files
git status
#remove from git repo
git commit -m "Remove unused code."
 
**=================================================================================**
#Renaming or moving files: 1. rename file in working dir 2. add and delete i.e stage both changes(new file and delete old)
ls
1. rename file in working dir
mv file1.txt main.c

git status
2.delete i.e stage change(delete old)
git add file1.txt
2. add i.e stage both change(add new file)
git add main.c
git status

# To rename and stage in single git command:
git mv main.c file1.c
git status
git commit -m "Refactor code."

**=================================================================================**
# getting short status of working dir and staging area:
git status -s

echo sky >> file1.c
echo sky > file2.c
git status -s

**--**
XY file1.c
XY file2.c

here X field tells staging area
     Y fields tells working area
**--**
git add file1.c

git status -s

echo ocean >> file1.c
git status -s
git add file1.c
git status -s

git add file2.c
git status -s

git commit -m "Add modified file1 and new file2."


**=================================================================================**


# Viewing the staged and unstaged changes:
note before commiting any code from staging area it has to be reviewed.
Now to locate the exact lines of code changed..?

# to compare working dir to staging area files i.e unstaged changes:
#Use the "git diff" command..!!!! to compare unstaged area files with with staged files
git diff
git status -s

code file1.c
and change first line and save
git status -s
git diff

#Use the "git diff --staged" command..!!!! to compare staging area files with git committed files
echo pacific ocean >> file1.c
git add file1.c
echo earth > file3.c
git add file3.c
git status -s

git diff --staged

**=================================================================================**

# visual diff tools:
kdiff3
p4merge
vscode
winmerge(windows only)
**=================================================================================**

# perform diff tool related configuration as shown begining:
git config --global diff.tool vscode
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
git config --global -e

**=================================================================================**

#to see unstaged chages
git difftool
#to see staged changes
git difftool --staged
**=================================================================================**
#viewing the history:
git log

git log --oneline
git log --oneline --reverse
git log --patch -1
git log --oneline --decorate
git log -p -1
**=================================================================================**
#GIT OBJECTS:
1. commits
2. Blobs(Files)
3. Tree(Directories)
4. Tags
**=================================================================================**
#viewing a commit:
to see diff 
git show <unique_identifier>
git show HEAD~1
git show HEAD~N  here N is number of step 1,2,3,4,......

# to see exact what is commited and not diff:

git show HEAD~1:.gitignore
git show HEAD~1:/bin/app.bin
git ls-tree HEAD~1
**=================================================================================**
#unstaging files: refer **5.1**
git restore --staged <fiename>
git restore --staged .
git status -s

# Discarding local changes: refer **5.2**
git restore <file>
git restore .
git status -s

# to remove untrracked files while discarding local changes:
git clean -fd
*-f or --force: force and -d: remove whole directories*
git status -s
**=================================================================================**
# restoring a file to an earlier version
*remove file from working directory and staging area*
git rm file1.txt
git status -s
git commit -m "deleted file1.txt"

# Now how to recover file deleted from both working directory and staging area .. ???
# Note: We can restore file from the last commit only
git log --oneline
#git restore basically restores from staging area and if not available there the from previous commit
git restore

#check "git restore -h"
git restore --source=HEAD~1 file1.txt
git status -s

**=================================================================================**

#create files:
echo hello > file1.txt
echo hello > file2.txt
#check git status:
git status

#add files/dir to staging area:
git add file1.txt file2.txt
git add *.txt
#adds entire dir to staging area
git add . 
git status
echo World >> file1.txtx
git status

git add file1.txt
git status


# how to commit:
git commit -m "Initial commit."
# if discription is longer
git commit and  enter
now editor opens and add a short description ideally less than 80 Char and close the editor window
git status
# commiting best practices:
# skipping the staging area:
Do if u know code is not required to be reviwed.
echo test >> file1.txt
git commit -a -m "Fix the bug that prevented user from signing up."
or
git commit -am "Fix the bug that prevented user from signing up."
**=======================4. create a branch =======================**
# to create a branch (if working on any new feature)
git branch -M <branch_name>
*Note: IF NO BRANCH IS CREATE THERE EXIST DEFAULT BRANCH NAMED master*
# to switch to new branch created
git checkout <branch_name>

# to create a branch and switch to it using single command
git checkout -b <branch_name>

#verify switch of branch or to which branch origin is pointing at
git branch
git branch -a
git branch -r	
git status 
or 
git status -b

# push git commit to git repo/remote
0. create a remote/repo in **github** and copy its url.
e.g: https://github.com/vikrant-sugandhi/test.git

1. add remote/repo 
git remote add <some_meaningfull_remote_name> <url_of_repo_or_remote_created_in_git>
e.g:
git remote add origin https://github.com/vikrant-sugandhi/test.git

2. to find where the origin is pointing
git remote -v

3. push git commit to git remote or repo
git push <remote_name> <branch_name>
e.g: git push -u origin main
**======================================3. HOW TO START ====================================**
## from github.com
**…or create a new repository on the command line**
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/vikrant-sugandhi/test.git
git remote -v
git push -u origin main

**…or push an existing repository from the command line**
git remote add <some_meaningfull_remote_name> <url_of_repo_or_remote_created_in_git>
e.g:
git remote add origin https://github.com/vikrant-sugandhi/test.git
git remote -v
git branch -M main
git push -u origin main
**===========================2. create .gitignore file ===================================**

#Ignoring files:
mkdir logs
echo hello > logs/dev.log
git status

# create .gitignore file in the root/parent of your project directory 
# and add all files names or extentions that are to be ignored as below 
# or using vi editor manually.
*create .gitignore in parent folder and type logs/ in it*
echo logs/ > .gitignore
> type: main.log
echo main.log > .gitignore
> type: *.log
echo *.log > .gitignore
or
vi .gitignore     and add all the files that are to be ignored here.
e.g
 logs/
 main.log
 *.log
 
 git status
 
# add git ignore to staging area
 git add .gitignore
 git commit -m "Add gitignore"
 
 **==========2.1 handle accidentally added unnecessary files and folders in git repo ===================**
# How to handle accidentally added unnecessary files and folders in git repo ?
#if wrongly added file e.g some bin file that is to be ignored in the git staging area:
 1. add file name to .gitignore 
 mkdir bin
 echo hello > bin/app.bin
 git status

# example here
*accidental commit as below:*
 git add .
 git commit -m "Add bin."
 
# how to handle this:
 1. add bin folder name to .gitignore 
 echo bin/ > .gitignore
   
git status

git add .
git commit -m "Include bin/ in gitignore."

echo helloworld > bin/app.bin

2. remove bin folder from only the staging area/Index (not from working dir)
**Note index means staging area**
git ls-files

git rm -h
git rm --cached bin/

git rm --cached -r bin/

git ls-files
git status

3. commit the changes
git commit -m "Remove bin dir that is accidentally committed."
echo test > bin/app.bin
git status
now the git will not track bin folder

**===============================1. ONE TIME CONFIGURATION IN A SYSTEM ==============================**
# After installing git in your system below configurations to be done:
# I did using vim editor
git config --global user.name "Vikrant Sugandhi"
git config --global user.email vikrant.sugandhi@gmail.com
# set default editor
git config --global core.editor "vim"
# tell git to wait untill i close editor
git config --global core.editor "code --wait"
# color options
git config --global color.ui auto
#for windows user
# git config --global core.autocrlf true
# for Linus and mac user
git config --global core.autocrlf input
# tool to user for diff commands
git config --global diff.tool vscode
# tell git to wait tilll I closes the tool for diff commands
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
# to display git config
git config --global -e


# cmd to check all setting/cofig: do this to verify all setting done as per list above
git config --list
git config --global --list

===============================================
# .git config files looks as below: 
[user]
 name = Vikrant Sugandhi
 email = vikrant.sugandhi
[core]
 autocrlf = input
 editor = code --wait
[filter "lfs"]
 clean = git-lfs clean -- %f
 smudge = git-lfs smudge -- %f
 process = git-lfs filter-process
 required = true
 [diff]
  tool = vscode
 [difftool "vscode"]
   cmd = "code --wait --diff $LOCAL $REMOTE"
===============================================

# how EOL is handled in windows and linux/mac:
windows : CR LF (true)
Linux or Mac : LR (input)

# getting help:
git <command> --help
git <command> -h
e.g:
git commit --help
git commit -h

git config --help
git config -h
