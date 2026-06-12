---
title: "how to install VBox Guest Additions in Upuntu 9.10"
date: 2009-12-05
forum: General Help
---

### Post by nichos on 2009-12-05
Hi

Host XP
VBox on it
Upuntu 9.10 in VBox.

I am not sure if I asked this recently.

Can not again install VBox Guest Additions in Upuntu 9.10. 

Read all about it & tried all help given including :-

cd /media/cdrom
sudo mount /dev/cdrom  /media/cdrom
sudo sh ./VBoxLinuxAdditions-amd64.run
sudo apt-get install build-essential linux-headers-generic

But all I get is as per attachment.

---

### Post by Bachstelze on 2009-12-05
Since you are running a 32bit Ubuntu, you must run

```
sudo sh ./VBoxLinuxAdditions-x86.run
```

---

### Post by nichos on 2009-12-05
That gives the same error.

thanx ...nick

---

### Post by howefield on 2009-12-05
Is your guest OS 64 bit ?

---

### Post by Dennis N on 2009-12-05
Simplest Way:

Use the Devices menu of the VirtualBox window:

```
Devices > Install Guest Additions
```

It should automatically run and do the installation.

Your screen shot shows VBOXADDITIONS_2. Current version is 3.0.12
Might be a good idea to upgrade VirtualBox.

---

### Post by howefield on 2009-12-05
> **Dennis N said:**
> Your screen shot shows VBOXADDITIONS_2. Current version is 3.0.12

Current version 3.1_3.1.0-55467  

[http://download.virtualbox.org/virtualbox/3.1.0/](http://download.virtualbox.org/virtualbox/3.1.0/)

---

### Post by nichos on 2009-12-05
thanx all,

I think I have 32, ordinary XP home sp3

Devices > Install Guest Additions is dead as a dodo mate, it does nothing.

Blast it all, I just downloaded the 3.1 & installed it, it deleted my old Sun directory & lost all the upuntu 9.10 hard work I did to get to the point I was in.
nick

---

### Post by howefield on 2009-12-05
> **nichos said:**
> I think I have 32, ordinary XP home sp3

You need the 32 bit guest additions for your 32 bit guest. Not the 64 bit that you were trying to install.

> ...it deleted my old Sun directory & lost all the upuntu 9.10 hard work I did to get to the point I was in.

Your virtual machine is likely still there, did you create it in the default /home/user/./Virtualbox folder ? 

Uninstalling virtualbox doesn't remove this folder and its contents.

---

### Post by Dennis N on 2009-12-05
> **nichos said:**
> thanx all,

Devices > Install Guest Additions is dead as a dodo mate, it does nothing.



Another way to start the guest additions installer:

Double click on the desktop icon for VB Guest Additions. In the window, look for 'autorun.sh', double click, then select the Run option.

---

### Post by Soul-Sing on 2009-12-05
```
cd /media/cdrom0
```
```
sudo bash ./VBoxLinuxAdditions-x86.run
```

---

### Post by nichos on 2009-12-05
SOLVED  thanx all

I reistalled 9.10 in the new 3.1 VBox.

I found the VBox references in C:\ but can do nothing within them.

Thanx Dennis for the promt,
although this is the upteenth time I tried the " sh ", this time did it.

I suppose will have to restart to work, & hopefully will not bother you on this again.

BTW I dual boot XP with Upuntu 8.4 & use XP mostly for FS9 & X, will this 9.10 be any better to upgrade to?
nick

---

