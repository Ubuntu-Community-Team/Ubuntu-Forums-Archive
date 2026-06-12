---
title: "System Restore Utility?"
date: 2010-04-04
forum: General Help
---

### Post by nerdtron on 2010-04-04
Is there a utility in Ubuntu 9.10 similar to the System Restore included by default on Windoze?
I will make major modifacations on my system and I want revert to my previous system in case something will go wrong...

---

### Post by Penguin Guy on 2010-04-04
There is nothing like that installed by default, but an application called [Simple Backup]("apt:sbackup") is included in the repositories - maybe that's what you're looking for?

---

### Post by nerdtron on 2010-04-04
Isn't this for files and directories data? I'm looking for a program to "remember the system files and configurations" and then it will be able to restore those settings when i choose them.

---

### Post by Penguin Guy on 2010-04-04
> **nerdtron said:**
> Isn't this for files and directories data? I'm looking for a program to "remember the system files and configurations" and then it will be able to restore those settings when i choose them.
I'm pretty sure there is no feature like that at the moment, and probably won't be for a long time because of the structure of Linux settings (all over the place). However, most important settings menus in Linux have [reset-default buttons]("http://ubuntuforums.org/attachment.php?attachmentid=152332&stc=1&d=1270394233") though, so it's hard to permanently mess up your system.

---

### Post by itiswhatitis on 2010-04-04
Not sure there is a tool to do this.  Here's what I do, probably much more elegant solutions out there...

I made a folder under one of my regular uses called backup.  In that folder, I reproduce the file structure to the file I am changing, I then copy the file there with an extension of the date I am changing the file. 

If I were editing the grub2 configuration:
/home/me/backup/etc/default/grub.04042010

Eventually, I have a lot of folders, and lots of files with different date extensions.  I think it makes a pretty good "restore point" for any changes I've made on a system going back to install.  Saved my bacon a few times...

---

### Post by blueridgedog on 2010-04-04
I use remastersys to make a snapshot of my system when I have it configured and when I make significant changes.  

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

