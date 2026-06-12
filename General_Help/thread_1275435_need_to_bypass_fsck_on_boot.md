---
title: "need to bypass fsck on boot"
date: 2009-09-25
forum: General Help
---

### Post by void64 on 2009-09-25
I'm running Xubuntu 2.6.24-24-386 as a Virtualbox guest on a Win XP x64 host. The Xubuntu systems runs a public web server ([www.open-aerospace.org]("http://www.open-aerospace.org")) which has been online a long time without system reboots.  I had been using the VB "save system state" functionality to pause the machine as needed when rebooting the host. Because of a VB upgrade, I had to finally shutdown the xubuntu server (worked fine). 

Now when I try to boot it, a fsck is forced and exits with "fsck died with exit status 4". I then get the option of going into a maintenance shell and running it manually. If I do, I get a blank screen and 100% CPU use, forever (at least for more than 8 hours).

What I need is a way to boot the machine without fsck being auto-run. Even if the file system is damaged, that way I'll at least be able to recover some of the data. I've found this page ([http://www.cyberciti.biz/faq/linux-unix-bypassing-fsck/](http://www.cyberciti.biz/faq/linux-unix-bypassing-fsck/)), and was hopeful but it didn't work. Grub seems to ignore the "fastboot" switch, and I cannot edit the fstab file because the file system is read-only after fsck dies and drops me in the maintenance shell.

Anybody have a suggestion on how to stop xubuntu from trying to run fsck during startup :confused:

---

### Post by ecmatter on 2009-09-25
Have you tried hitting 'esc' during the fsck?  That should let you cancel the file system check.

---

### Post by void64 on 2009-09-25
> **ecmatter said:**
> Have you tried hitting 'esc' during the fsck?  That should let you cancel the file system check.

It goes by very fast - I've tried hitting esc at the right spot but assuming I hit it at the right time it still didn't do anything. Thanks for the suggestion though ...

---

### Post by dreamingdarkness on 2009-09-25
Have you tried the steps on [http://ubuntuforums.org/showthread.php?t=163500?](http://ubuntuforums.org/showthread.php?t=163500?)

Did you set the /etc/fstab to have the '0 0' not the other settings?
You can do this with a livedisk, if you can't get the desktop to boot.

If so, might need to post more info, and hopefully someone more familiar with the fsck/disk-checks will be able to help you out.

---

