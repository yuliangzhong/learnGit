# Git

## Beginner Level: File Tracking

```bash
##### install git #####

##### register account #####
$ git config --global user.name "YourGitHubUserName"
$ git config --global user.email "YourGitHubRegisteredEmail@example.com"
# set ssh connection in /
$ ssh-keygen -t rsa -C "YourGitHubRegisteredEmail@example.com"

##### from PC to Github #####
# in GitHub, build a new repo without readme, then you can see instructions

$ git init # build git repo!
$ git add file1.txt # add file1.txt **(stage/index)**
$ git add . # add all files
$ git commit -m "first commit" # commit all added files with comments **(to save)**
$ git status # always can use this cmd to check git repo status
# do some revision
$ git status
$ git diff file1.txt # check difference, use "space key" to see more
$ git restore file1.txt # discard revision, to last add/committed version
# add/commit file... do revision... add/commit file...

$ git log # to see all commit logs
$ git reset --hard HEAD^ # come back to last commit & clear later commits
$ git reset --hard f9028 # come back to snap f9028 & clear later commits
$ git reflog # to find commit version number

$ git branch -M main # change branch name
$ git remote add origin git@github.com:yuliangzhong/learnGit.git
$ git push -u origin main # push changes & link repos, add "-u" for first time
# origin: name of the remote repo
$ git remote rm origin # disconnect remote repo

##### clone code from Github #####
$ git clone git@github.com:yuliangzhong/learnGit.git # don't use https anymore!
```

## Median Level: Branch Control & Cooperation

```bash
$ git branch # check all local branches
$ git branch -a # check all branches (incl. remote)
$ git branch develop # init "develop" branch locally, **from current branch**
$ git checkout release # switch branch to "release"
$ git checkout -b release # init branch "release" locally then switch to it
$ git checkout -b dev origin/dev # init branch "dev" from remote repo "dev"
# do some work... git add... git commit...

$ git merge feature # merge branch "feature" **to current branch**
$ git merge --no-ff feature # no fast-forward merge
$ git diff dev # compare difference with branch "dev"
$ git diff origin/main # compare difference with remote branch "main"
$ git branch -d feature # delete local branch "feature"
$ git push origin dev # push current branch to remote repo in "dev" branch

##### cooperate with others #####
$ git push origin <branch-name> 
$ git pull origin <branch-name> # merge origin branch with current branch
$ git branch --set-upstream-to <branch-name> origin/<branch-name> # setup link

##### GitHub #####
# * fork (get read and write permission) / git clone
# * pull request
# * issue
# * explore
```

## Advanced Level: some Git Features

```bash
##### fix emergency bugs #####
# I am doing my work... Suddenly, I need to fix some bugs
$ git stash # save unadded working repo of current branch
# checkout to main, new branch, fix bug, commit, merge to main, delete branch
# checkout back to current branch
$ git stash list
$ git stash apply # apply latest stash
$ git stash apply stash@{0} # apply specific stash
$ git stash drop # delete stash
$ git stash pop # apply and drop
# Continue my work...

$ git cherry-pick 4c805e2 # merge a specific commit (bug fix) to current branch

##### git log #####
$ git log --graph --pretty=oneline --abbrev-commit

##### organize commit logs #####
$ git rebase release
# If conflicts pop up, solve them
$ git add .
$ git rebase --continue

##### force push #####
$ git push -f origin main # -f means FORCE

##### tags #####
$ git tag v1.0.1.RELEASE # init a tag to latest commit in current branch
$ git tag # see all tags
$ git tag -a v0.1 -m "version 0.1 released" 1094adb # tag specific commit
$ git tag -d v1.o # delete tags
$ git show v1.0 # show tag info

##### gitignore #####
# in file .gitignore or .gitignore_global
.DS_Store # ignore .DS_Store
$ git add -f test.txt # force add
$ git check-ignore -v App.class # why ignored?

##### alias #####
# use git lg for better views
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

##### submodule #####
$ git clone --recursive git@github.com:user/project.git # clone
$ git submodule update --init --recursive # first pull with submodule
$ git submodule update --recursive --remote # update submodule
```

## Master Level: Keep Git Workflow

- Origin = { main, release, develop }
- Version number: V(0.1.0.RELEASE)
    
    main version + sub version + feature version + environment
    

### **In my project:**

- **dev → dev/yuzhong [main] (local / remote)**
- **dev/yuzhong → feature/xxx [dev] (local / remote)**
    
    **work on feature/xxx, test it, (—no-ff) merge feature/xxx → dev/yuzhong**
    
- **project done, (—no-ff) merge dev/yuzhong → dev**

---

### References:

- git class

[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)

- git command cheatsheet

[](https://liaoxuefeng.gitee.io/resource.liaoxuefeng.com/git/git-cheat-sheet.pdf)

- git workflow

[10年经验17张图带你进入gitflow企业项目代码版本管理的最佳实践](https://www.cnblogs.com/tomakemyself/p/13829985.html)

[Git 使用规范流程](https://www.ruanyifeng.com/blog/2015/08/git-use-process.html)