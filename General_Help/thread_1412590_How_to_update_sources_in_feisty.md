---
title: "How to update sources in feisty"
date: 2010-02-21
forum: General Help
---

### Post by eeprom on 2010-02-21
Hello,
I'm trying to update my sources so that I can download some software.  I am running Ubuntu 7.04.  In another post, I was given this link for updating my source list.   [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
I have download quite a few files from this ftp, I've manually edited my sources list, and by sheer luck my system is still running.  Can someone please explain what steps I need to take in order to update my sources?

thanks,
EE

---

### Post by RedSquirrel on 2010-02-21
> **eeprom said:**
> I am running Ubuntu 7.04.

:-k

Why are you running an Ubuntu release that is no longer supported with security updates?

---

### Post by Swagman on 2010-02-21
bump

gimme a couple of minutes to live boot into Feisty Fawn

IThe only reason I kept this cd is because I printed a kewl disc cover for it !!

---

### Post by sports fan Matt on 2010-02-21
I am shocked--& Agree with Red Squirrel..I'd at least if it were me, backup and at the very minimum upgrade to Hardy Heron 8.04.  Is there a particular reason why the ftp files wouldnt work with Hardy?

---

### Post by Swagman on 2010-02-21
Back ...wow.. this is horrible. Had to use safe graphics mode because X don't like my GTX8800 on this distro and everything is..BIG!!

ok.. I tried to take a screengrab but prtscn doesn't like to multitask in this so I cant grab with the menu open.

Trying to install Ksnapshot fails to find the repository.

so.. 

Go into System/administration/software sources and you should get this screen

[http://www.upload3r.com/serve/210210/1266780661.png](http://www.upload3r.com/serve/210210/1266780661.png)

sorry about the png... that's all that's available !!

just select the universe & multiverse.

Ok.. I'm getting out of here... Tiz scary !!

At least you will appreciate Lucid Lynx when you fresh install in a couple of months

[edit]

Gentlemen, he's using Feisty because he bought a book recently with it on. He wasn't any the wiser. He might as well stay on it until Lucid Lynx is released because the upgrade path is not direct unless he clean installs.

Ok.. Back in 9:10 (Karmic) that's MUCH better. The sources.lst is the same. I caouldn't remember if they were and that's why I booted into Feisty.

This is how that screengrab looks in Karmic

 [http://www.upload3r.com/serve/210210/1266781154.jpeg](http://www.upload3r.com/serve/210210/1266781154.jpeg)

---

### Post by eeprom on 2010-02-21
About using Feisty...right now I am only concerned with learning how to use linux.  I am using an old computer which doesn't even have enough ram to run the OS properly.  I have nothing on this computer that is of any value.  My goal at this point is to learn.  In a few months, I'll get another computer and start off clean with Jackal.

About updating the source files...
I tried to update using universe and multiverse, and I get the same errors, all of them related to "File Not Found".  It seems that the path of the sources is no longer valid.  Is there a way to simply download a new source.list, then save the original as a backup, and then install the new one in /etc/apt?

---

### Post by Swagman on 2010-02-21
Press alt F2 and enter 

```
gksudo gedit
```

You are now in admin mode. Navigate to etc/apt and load sources.list

Whatever edits you  make in it can now be saved.

I don't know where Feistys repositorys are. Sorry

When you have saved out the new sources open a terminal and enter

```
 sudo apt-get update
```
then
```
sudo apt-get upgrade
```

---

### Post by kostkon on 2010-02-21
Check [here]("https://help.ubuntu.com/community/EOLUpgrades") for the changes you'll have to make to your software sources list.

---

### Post by dcstar on 2010-02-21
> **Swagman said:**
> 
........
I don't know where Feistys repositorys are. Sorry
........

There are **NO** repositories for unsupported releases.

---

### Post by Swagman on 2010-02-22
> **kostkon said:**
> Check [here]("https://help.ubuntu.com/community/EOLUpgrades") for the changes you'll have to make to your software sources list.

That is a useful link but looks to be a heck of a lot of faffing about.

As Eeprom has revealed it's just a test machine I now recommend he downloads 9:10 and clean installs that.

At least he'll gain experience using gparted to remove partitions etc !!

---

### Post by slakkie on 2010-02-22
> **dcstar said:**
> There are **NO** repositories for unsupported releases.

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) says otherwise.

> **Swagman said:**
> That is a useful link but looks to be a heck of a lot of faffing about.

As Eeprom has revealed it's just a test machine I now recommend he downloads 9:10 and clean installs that.

At least he'll gain experience using gparted to remove partitions etc !!

The upgrade is really simple to execute and there is no faffing in the guide. It actually just works, copy/paste and done.

---

### Post by theozzlives on 2010-02-22
Feisty has reached End Of Life for quite awhile. You can't update sources. Do yourself a favor and use learn Linux on a version that still works.

---

### Post by slakkie on 2010-02-22
> **theozzlives said:**
> Feisty has reached End Of Life for quite awhile. You can't update sources. Do yourself a favor and use learn Linux on a version that still works.

You can update sources on unsupported version. And the unsupported versions of Ubuntu still work.

---

