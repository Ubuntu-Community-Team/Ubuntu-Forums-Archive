---
title: "Can't install program in wine - don't have permission"
date: 2010-04-27
forum: General Help
---

### Post by FireFighter on 2010-04-27
I have wine installed on Ubuntu 10.04. I am trying to get Quicken 2004 installed with the installation cd. I open the cd to go to the Install.exe file. Right click on the that file and tell it to: Open with wine windows program loader. I get the following window::( 

The file '/media/QW04BASR1/install.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Ok, I go to read about executable bit. Looks like I need to change the permission of it. Won't let me do it. Says: 

Sorry, could not change the permissions of "install.exe": Error setting permissions: Read-only file system:(

Ok, look up and see that it is a read only. Click to change that to the only other option: Read & Write. Get the following: 

Sorry, could not change the permissions of "install.exe": Error setting permissions: Read-only file system:(

What do I need to do here? I have never had this problem installing Quicken in wine before using previous versions of Ubuntu.:confused:

Any/all help appreciated!

---

### Post by mc4man on 2010-04-27
Several ways around this, but for the moment - r. click on the Install.exe  -> open with other application -> use a custom command
For the command simply type
  wine

edit:
various methods (post 11
[http://ubuntuforums.org/showthread.php?p=9119462#post9119462](http://ubuntuforums.org/showthread.php?p=9119462#post9119462)

partial explanation
[http://ubuntuforums.org/showthread.php?p=9141228#post9141228](http://ubuntuforums.org/showthread.php?p=9141228#post9141228)

---

### Post by overlordchin on 2010-04-27
try 

```
sudo wine /media/QW04BASR1/install.exe
```

Not 100% sure you need the sudo. You can try it first without it if you like.

---

### Post by oleink on 2010-04-27
In terminal go into the directory "QW04BASR1" and type sudo chmod a+rwx install.exe

After that try installing it

---

### Post by oleink on 2010-04-27
Should work after that

---

### Post by FireFighter on 2010-04-29
Thanks! Both of your advices worked and were used. For anyone who might be needing to know what was done, this is how I got it to work. In terminal:

(1) Changed to the directory:  cd /media/QW04BASR1

(2) Typed: sudo chmod a+rwx install.exe

It asked for my password. After entering that and hitting enter:

(3) Typed: wine /media/QW04BASR1/install.exe

It started the process and all seems well. Just a note. I did have to install wine 1.0 and not use the new beta version to get this particular Windows program to install.

Again thanks so much!

---

### Post by 73ckn797 on 2010-05-06
> **FireFighter said:**
> Thanks! Both of your advices worked and were used. For anyone who might be needing to know what was done, this is how I got it to work. In terminal:

(1) Changed to the directory:  cd /media/QW04BASR1

(2) Typed: sudo chmod a+rwx install.exe

It asked for my password. After entering that and hitting enter:

(3) Typed: wine /media/QW04BASR1/install.exe

It started the process and all seems well. Just a note. I did have to install wine 1.0 and not use the new beta version to get this particular Windows program to install.

Again thanks so much!


[SIZE=2]I was having the same problem with 10.04 and this fixed it. Thanks.[/SIZE]

All of the Wine programs worked after upgrade but Quicken started having glitches. I performed a fresh install and ran into this problem. I also used Wine 1.0 and not 1.2.

---

