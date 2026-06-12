---
title: "sudo command problem"
date: 2009-09-07
forum: General Help
---

### Post by harryliddic on 2009-09-07
I am trying to go back to and older version of amarok and the instructions I received from a useful website( Ubuntu Geek) said the first command I should run is "sudo gedit/etc/apt/source.list" I know gedit is in there because I used it before.  But I get a "command not found" error mesaage. what could I be doing wrong. Here are the instructions 



        Add GPG key

    * Goto Terminal and copy-paste the following.

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AE74AE63

    * Done.

Add PPA Repo

    * Open /etc/apt/sources.list

sudo gedit /etc/apt/sources.list

    * And copy paste the followng repo into sources.list file.

deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main

Install Amarok 1.4 in Ubuntu Jaunty

    * Before installing Amarok 1.4, do remove old amarok to undo any conflicts.

sudo apt-get remove amarok

    * Now install Amarok 1.4 in your Ubuntu Jaunty

sudo apt-get install amarok14

    * Done!

---

### Post by Bachstelze on 2009-09-07
> **harryliddic said:**
> I am trying to go back to and older version of amarok and the instructions I received from a useful website( Ubuntu Geek) said the first command I should run is "sudo gedit/etc/apt/source.list" I know gedit is in there because I used it before.

You missed a space. ;)

---

### Post by SuperSonic4 on 2009-09-07
ubuntu geek told you to use sudo for a GUI app? gksu is a better idea

---

### Post by PixelSmack on 2009-09-07
> **SuperSonic4 said:**
> ubuntu geek told you to use sudo for a GUI app? gksu is a better idea

Should this be gksudo? however yes i think you are right.

---

### Post by DaithiF on 2009-09-07
gksudo is an alias to gksu

```
ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2009-06-30 20:53 /usr/bin/gksudo -> gksu

```

---

### Post by ddrichardson on 2009-09-07
Like HFL said:
```
gksu gedit /etc/apt/source.list
```
gksu is better practice but in this case it's fairly academic.

---

