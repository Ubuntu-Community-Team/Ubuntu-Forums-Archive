---
title: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct..."
date: 2011-06-28
forum: General Help
---

### Post by trmnshwrx on 2011-06-28
I found <a href="http://ubuntuforums.org/showthread.php?t=388348">this</a> thread, but I still run into trouble.  Here's what I get when I run 'sudo dpkg --configure -a' (everything in-between the stars):

**********************************************************************
warning, in file '/var/lib/dpkg/available' near line 43882 package 'virtualbox-3.1':
  error in Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
Setting up noip2 (2.1.9-3) . . .

Auto configuration for Linux client of no-ip.com.

2 hosts are registered to this account.
Do you wish to have them all updated?[N] (y/N)
**********************************************************************

...And when I choose either y/n, it just hangs up forever. HELP! I can't install or uninstall anything! Synaptic Package Manger won't run. I can't do it manually, either...

What can I do?

---

### Post by derklempner on 2011-06-28
Delete all the files in **/var/lib/dpkg/updates** and try reinstalling the VirtualBox package from scratch.

---

### Post by trmnshwrx on 2011-06-29
Will this re-enable me to install things? I'm not so concerned about VirtualBox; I actually tried to uninstall it in order to get around this error, but I can't do that.

---

### Post by trizrK on 2011-06-29
> **trmnshwrx said:**
> Will this re-enable me to install things? I'm not so concerned about VirtualBox; I actually tried to uninstall it in order to get around this error, but I can't do that.
In short,
Yes, it will.

---

### Post by trmnshwrx on 2011-06-29
Nothing there in the first place. I even opened nautilus from root to see. It's empty.

---

### Post by derklempner on 2011-06-29
> **trmnshwrx said:**
> Will this re-enable me to install things? I'm not so concerned about VirtualBox; I actually tried to uninstall it in order to get around this error, but I can't do that.
It's possible that **/var/lib/dpkg/available** may have somehow become corrupted, but you should have a backup of that file in the same directory, named **available-old**.  Delete **available** and run **sudo apt-get update**.  Then try to install a package.

If that doesn't fix your problem, do it again, and as a third step delete all files in **/var/lib/dpkg/updates** BEFORE you try to install another package.

---

### Post by trmnshwrx on 2011-06-29
Thanks! It still told me that it couldn't get an exclusive lock...and that was after sudo rm var/lib/apt/lists/lock ... Anyway, so I rebooted, ran apt-get update, and now I'm actually upgrading to Natty Narwhal.

---

### Post by trmnshwrx on 2011-06-29
(aborted, once my computer found out how much disk space Natty wants...but at least my initial problem was fixed...)

---

### Post by Raziel14 on 2012-02-26
Hi, I am unable to delete /var/lib/dpkg/available  or anything from file system except home folder, is there a way to setup permission to do it? tnx

---

### Post by iMetaphysikz on 2012-02-26
> **Raziel14 said:**
> Hi, I am unable to delete /var/lib/dpkg/available  or anything from file system except home folder, is there a way to setup permission to do it? tnx

Are you in the sudoers group? if so just do:
sudo rm /var/lib/dpkg/available

if you just want access to the files you would have to chmod it to the correct permissions, for everyone on the system it would be:
sudo chmod 777  /var/lib/dpkg/available

---

### Post by poorig on 2013-03-20
i had same problem, but i had problem with flash plugin. you can do this first do this

apt-get install 'somthing like bind9 (not important)'

then u see a message 

 dpkg --configure -a

then you have to copy name of pakage u r installing i think for u is virtualbox 

then 

apt-get remove 'pakage name'

i did this and it's ok now!

---

### Post by varunendra on 2013-03-20
Old thread closed.

---

