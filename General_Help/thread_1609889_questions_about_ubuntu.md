---
title: "questions about ubuntu"
date: 2010-10-30
forum: General Help
---

### Post by coreyscx on 2010-10-30
1. what does sudo apt-get install update do??
2. what are repositorys??
3. do most games like fallout work on wine??

thanks guys :)

---

### Post by trikster_x on 2010-10-31
> 1. what does sudo apt-get install update do??
I think you are referring to "sudo apt-get update".  What it does is it update the package list for the "apt package manager", so it knows which programs have updates available.

> 2. what are repositorys??
A repository is a server that gives a package manager the information and files it needs to install and update a program.  Some repositories are not maintained with the most up to date versions of a program, so sometimes it is necessary to add a repository from the developer of the program.  Care should be taken when doing this, since the newer versions are not always 100% compatible with Ubuntu (see problems with the compiz repos as of late).  Sometimes it is necessary to install a repository just to be able to install a piece of software, though this is rare for the average user.

> 3. do most games like fallout work on wine??
[http://appdb.winehq.org/]("http://appdb.winehq.org/") is a database of software that has been tested with wine.  Some games work great out of the box, and others take some major tweaking to get them to work right, if at all.  As of the most current version of wine, Fallout 3 is on the gold list, which means that you can run it with most features available.  Keep in mind that sometimes it is because the test machine simply isn't capable of the features, especially games with high graphics requirements, so you should always read the notes on a specific game.

---

