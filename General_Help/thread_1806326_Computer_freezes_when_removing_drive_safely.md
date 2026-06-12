---
title: "Computer freezes when removing drive safely"
date: 2011-07-17
forum: General Help
---

### Post by xcrunner78 on 2011-07-17
Hi,

I'm having a problem that is slightly irritating.  I lost a document because of this on Libre Office.  Wen I go to remove my external drive, I always right click the icon, then go to "Safely Remove Drive."  After doing this my computer freezes, or a the screen goes blank (and my cap lock and scroll lock lights start flashing).  This has happened two other times, while I was on the Internet.  I have to hold down the power button to shut down the computer.  Any suggestions on why this is happening or how to fix it.  I lost a document because this happened.  The document was already saved and when reopening it it was blank.

Any help would be much appreciated!

Jason

---

### Post by politas on 2011-07-19
This is happening to me, too, ever since the latest kernel upgrade to 2.6.32.33.39.  I Right-click an external drive on the desktop, choose "Safely remove drive", and and my entire system locks up, requiring a hard power-off. I've looked in /var/log/messages, and there is literally not a single entry for the time that the system locked up. There are regular entries from the previous evening, then the power-up messages after I reset.

This has happened with a couple of different external hard drives, one self-powered and one USB-powered, so it doesn't appear to be a problem with the hard drive. 

This is a serious issue that needs to be dealt with quickly.

---

### Post by politas on 2011-07-19
Oh, I should add that I did manage to avoid this one time by using the Disk Utility to unmount and then safely remove one of my drives.

---

### Post by xcrunner78 on 2011-07-25
Politas, I found that a bug was filed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

also this was posted:

[http://ubuntuforums.org/showthread.php?p=11085203](http://ubuntuforums.org/showthread.php?p=11085203)

I hope that this is helpful...I would like to rollback my kernel for the time...any idea on how to do this?

---

### Post by politas on 2011-07-25
Ah, yes. Sorry, should have reported that bug back to this thread for you. I've been posting comments on that a bit, trying to help nut out the exact issue.

To rollback your kernel, the easiest method is to change your "Default Operating System" in System > Administration -> StartUp-Manager. Choose the previous kernel entry (2.6.32-32) that DOESN'T say "(recovery mode)".

---

### Post by Rideen on 2011-09-30
Hi, I am absolute beginner to ubuntu and got this bug as well.

What command do I need to run in order to get this bug fixed (to download the fix)?

I did 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Is this gonna do it?

---

### Post by xcrunner78 on 2011-09-30
I haven't had this problem with the newest kernal 2.6.32-34.  Therefor I thought that it was a kernal problem.  You could roll-back your kernal in start-up manager to something that is not a recoevry mode kernal:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

I hope that this helps.

---

### Post by Rideen on 2011-09-30
Indeed, this issue has been resolved in 2.6.32-34 and after I have updated, everything is just fine!

Thanks.

---

