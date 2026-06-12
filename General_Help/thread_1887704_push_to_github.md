---
title: "push to github"
date: 2011-11-27
forum: General Help
---

### Post by gishaust on 2011-11-27
hi Ubuntu lovers 

I have been learning git and git hub on Ubuntu 11.04 I have followed the tutorials  and got it to the point where I have created a local repository added files and directories to it and have moved my first read me file to git hub.

I know the following works and have added to my project to the local repository by using the following commands and every works fine. 
```

  357  git add logic
  358  git status
  359  git commit -a
  360  git status
  361  git add licence
  362  git add licence.txt

```

So I decide if to try and add it to git hub by the push command
and got this
```

The program 'push' is currently not installed.  You can install it by typing:
sudo apt-get install heimdal-clients


```

I know that accessing git hub works as I have already add to the github repository because of the commands below (me has been replaced)
```

 321  git config --global user.name "me"
  322  git config --global user.email me@gmail.com
  323  cd ~/website/me
  324  git init
  325  ls
  326  git add readme
  327  git add README
  328  git commit -m 'first commit'
  329  git remote add origin git@github.com:me/me.git


```

What I am trying to do is push the whole local repository into git hub but I not sure how to do this from the command line can anyone give me a hint?

---

### Post by gishaust on 2011-11-27
found it git push master

---

