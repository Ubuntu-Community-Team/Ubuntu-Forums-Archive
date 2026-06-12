---
title: "Repository error?"
date: 2010-02-17
forum: General Help
---

### Post by sububtu on 2010-02-17
[SIZE=4][COLOR=Red][SIZE=3][COLOR=Black]im unable to update /install packages, when ever i try to install/update i got this message.[/COLOR][/SIZE][/COLOR][B][COLOR=Red]


Could not download all repository indexes[/COLOR][/B][/SIZE]

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by s.fox on 2010-02-17
Hello,

Can you post the contents of your /etc/apt/sources.list file?

-Silver Fox

---

### Post by geirha on 2010-02-17
This is Ubuntu 9.10? It could be that the mirror you are using is down. Go to System -> Administration -> Software Sources and select a different server in the «Download from» drop-down box. When you close the Software Sources window, a new dialog will appear; click the Reload button on that.

---

### Post by sububtu on 2010-02-17
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe

---

### Post by sububtu on 2010-02-17
[SIZE=4][COLOR=Black]**Ubuntu Server Edition,**[/COLOR][/SIZE]

---

### Post by geirha on 2010-02-17
Support for Ubuntu 7.04 Feisty Fawn ended october 2008. The feisty repositories are not available anymore. There is an archive of it that can be used to upgrade to Ubuntu 7.10, and then to 8.04. Ubuntu 8.04 Server will be supported until april 2013.

See this for information on how to upgrade. [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

