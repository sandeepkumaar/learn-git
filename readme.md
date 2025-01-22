## Git merge
```
$ git checkout master
$ git merge feature
```
Read as `merge master with feature with master leading`

## stage
```
$git add .
$git add -p #break the diffs and stage them individually. 's' to split
```

Stage this hunk [y,n,a,d,/,j,J,g,e,?]? ?
y - stage this hunk
n - do not stage this hunk
a - stage this and all the remaining hunks in the file
d - do not stage this hunk nor any of the remaining hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help

## Unstage a staged file

```
$ git reset HEAD <filename>
```

Note: 
HEAD / HEAD@{0}, HEAD@{1}, HEAD@{2} refers to commits of the switched branch from latest.

$ git reflog // says it

## Unmodifying a Staged file
```
$ git checkout -- <filename> #checkout from committed file
```

## Reset 

HEAD : Last commit on the current branch
Index: staged files; to be committed
Working Directory:  untracked; tracked but not committed files



> Switching branches or cloning goes through a similar process. 
> When you checkout a branch, it changes HEAD to point to the new branch ref, 
> populates your index with the *snapshot of that commit*, 
> then copies the contents of the index into your working Directory.

When switched all the 3 tree will have the same file content. 
git status will show when there is a difference


### $ git reset --soft `<HEAD>`
moves the HEAD and the **Branch** to the commit **`<HEAD>`** points to 
Leaving the Index, Working dir intact as it were before the command
> git move HEAD~


### $ git reset --mixed `<HEAD>` // default // $ git reset HEAD~
moves the HEAD and **Branch**
unstage the files that were staged
Leaves the working dir intact as it were
> git move HEAD~
> git unstage 


### $ git reset --hard `<HEAD>`
moves HEAD and **Branch** 
unstage the files that were staged
**re-writes** working dir with contents of the prev commit
> git move HEAD~
> git unstage
> git checkout HEAD~


### Git Squashing: squash a set of commit to a single commit
``
$ git reset --soft <HEAD>
``
Moves the HEAD and Branch to the `<HEAD>` pointing to with index and working having 
all the latest commit changes. 
Now,
`` $ git commit ``` creates a new commit from that branch with all the changes sqashed.
Leaving the other commits clipped??




## Git rebase

git rebase <branch you want to move to> <feature's base> <feature>
```
$git rebase master feature #when feature'sBase=Master
$ git rebase --onto master base feature

Note:  
when rebase results in merge conflicts, resolve the conflict, stage the 
resolved file and do `rebase --continue`

```
$ git add file
$ git rebase --continue
```
when base branch and feature's base are same

```
git rebase --onto dev dev feat

#is equivalent to 
git rebase dev feat
```


## git diff
```
$ git diff base feature
$ git diff --name-only
$ git diff --stat
$ git diff branch1 branch2 -- file-name
```

## git stash
Useful
- to quickly wrap ur code to checkout other branch
- to apply some config code for certain env/cases
```
$ git stash save <name>
$ git stash list
$ git stash apply/pop stash@{0}
$ git stash show -p  #show stash contents
$ git stash drop stash{}
```
## git remote
```
$ git remote add ''
$ git remote rename name1 name2
$ git remote set-url origin 'url' / edit origin url

```
## git tag
two ways
- ligth tags // use for temporary preferably in local repo
- annotated // use for tracking versions. shared between local/remote

```
$ git tag v1.1  #light
$ git tag -a v1.1 -m ""  #annotated
```
Other useful commands
```
$ git tag   #list tags
$ git show <tag>  #tag info 
$ git push origin <tagname>   #push tag to remote
$ git push origin --tags   #push all tags to remote
$ git tag -d <tag>  #delete tag
$ git push origin --delete <tag>  #delete tag from remote
$ git checkout <tag>
```
## git config
```
$ git config --global/local/system --list
$ git config <env> http.proxy ''
$ git config >env> http.proxy // getter
$ git config unset 
```


## Ref
- https://git-scm.com/book/en/v2/Git-Branching-Rebasing
- https://git-scm.com/book/en/v2/Git-Basics-Tagging


