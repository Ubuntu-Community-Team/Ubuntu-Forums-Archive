---
title: "wtf!! i can't boot ubuntu anymore!"
date: 2006-03-14
forum: General Help
---

### Post by groggyboy on 2006-03-14
So, a big case of human error here.  From what I gather, I somehow made my ubuntu partition read-only.  And let me tell you, ubuntu does NOT like that!

Here's the story:  I had just installed a program in windows called [fs-driver]("http://www.fs-driver.org/") which is supposed to let me access ext2 and ext3 partitions from my windows partition.  When I rebooted to ubuntu, it got all the way to the gnome display manager, and then crashed, throwing me into a console.  from the console, i couldn't do anything.  every time i tried sudo startx or sudo reboot or sudo anything, it said I didn't have read-write permissions!  So I went back to windows and uninstalled fs-driver.  Then when I booted back into ubuntu, the startup got to the point where it says "checking root file system", and then this came up (possibly not exact because i copied it by hand):
> Ubuntu contains a filesystem with errors, check forced.
*performs check*
Duplicate or bad block in use!
Ubuntu: Multiply-claimed block(s) in inode 393237:797406
Ubuntu: Multiply-claimed block(s) in inode 393516:797406
Ubuntu: (There are 2 inodes containing multiply-claimed blocks.)

Ubuntu: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
[[COLOR=Red]fail[/COLOR]]
[COLOR=Red]*[/COLOR]fsck failed.  Please repair manually and reboot. Please note
[COLOR=Red]*[/COLOR]that the filesystem is currently mounted read-only.  To
[COLOR=Red]*[/COLOR]remount it read-write:
[COLOR=Red]*[/COLOR]       #mount -n -o remount,rw /
[COLOR=Red]*[/COLOR]CONTROL-D will exit from this shell and REBOOT the system.

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#_ So I typed "mount -n -o remount,rw /".  and rebooted.  Same thing.  So I rebooted again, this time in recovery mode, and I still got the same thing.

Just to state the obvious, it would appear I have taken away all read-write priveleges in ubuntu.  Any idea how to fix this?  Maybe from my Ubuntu dvd (or knoppix)?  Warning: i'm still a noob, i've only had ubuntu for a month, and aside from the aforementioned knoppix cd, it is my first go with linux.  Any help is much appreciated, but don't get too technical on me.

I throw myself at the mercy of the mighty forums.  HELP ME!
:edit:

---

### Post by matthew on 2006-03-14
Hopefully someone will be able to help you with your problem here shortly...in the meanwhile I need to remind you that there are certain acronyms that are not appropriate for use in these forums according to the policy you read when you signed up. I modified your thread's title. Here's a gentle reminder.

[http://ubuntuforums.org/index.php?page=policy]("http://ubuntuforums.org/index.php?page=policy")

Thank you and enjoy your stay in the forums. I hope you get an answer soon.

---

### Post by groggyboy on 2006-03-15
sorry.  i've edited it.

---

### Post by bixin on 2006-04-11
I had this problem last night, well the privilege loosing part. What I did to get it back was:

1. load ubuntu in recovery mode
    press esc while  Grub is loading and choose recovery mode
2. open terminal and typed
   sudo chown myusername /what i want to own again

I happened to have given away the privilege of using the /usr files but once I restored that everything seemed okay, my gui login disappeard which i am still fixing but everything seems to be as it was. You probably know this but in recovery mode you have the keys to the kingdom, use them wisely. 

Disclaimer**** Our problems may be diffrent, and I am not an expert but this is how I got back into Ubuntu my .02:KS

---

### Post by jdong on 2006-04-11
Ok, your Ubuntu filesystem has been corrupted by this driver. The filesystem checker you see running there is in what's considered "preen" or "automatic" mode -- done on bootup if something wrong is detected with the drive.

It's meant to do minor cleanups and fixes, but when it stumbles upon a big problem, it'll back off for safety reasons. You will need to manually start the checker.

When it drops you to the root prompt, type in **fsck -y**, and let it complete. Hopefully, the system will be in usable condition afterwards, but that may not be  the case. If you cannot boot after repairs are made, your best bet is to use a LiveCD to pull off any personal data you have intact, then reinstall.

---

