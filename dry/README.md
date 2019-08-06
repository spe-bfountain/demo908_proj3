# demo908_common
this is the code we share across our various projects


## Instructions

With subtrees, we use commands and patterns of workflow that are much more similar to the straight repo, instead of all the additional complexity involved with git submodules.

The main caveat I have gleaned is that from the command line we need to pay attention to the current working directory: commits are from INSIDE the dir checked out from the common repo (cd proj1/dry), while the pulling and pushing needs to be from OUTSIDE that common dir (cd ~/proj1).

One other little caveat is that if we used "squash" initially to omit common history when setting up the subtree, then we also use "squash" every time we pull after that.

### Pulling before making changes
_be sure to only do pulling and pushing from OUTSIDE the common subtree dir_ 

cd proj1 ;
git subtree pull --prefix dry dry master --squash ;

### Making changes, staging, committing
_be sure to only do this committing from INSIDE the common subtree dir_

cd dry ;

touch new4common ; 
git add new4common ; 
git commit -m "add new file to common code, from a project" new4common

vim hap.py ;
git add hap.py ;
git commit -m "edit the commonly-referenced hap.py file, from a project" hap.py

### Pushing after making changes
_be sure to only do pulling and pushing from OUTSIDE the common subtree dir_

cd .. ;

git push origin master ;
git subtree push --prefix dry dry master ;


### :b

