---
title: "Karmic won't shut down...And reports HD as Failing"
date: 2009-11-01
forum: General Help
---

### Post by YosefKaro on 2009-11-01
Please help, Karmic won't shut down or reboot: I always have to manually press the power button.  Karmic is an upgrade on wubi.  Any suggestions would be appreciated.

Another problem I am having is that on start up, Karmic is saying that my HD is failing: that it has 82 bad sectors...I ran several diagnostic checks and they all report that my HD is in perfect health.  Could this false alarm be caused because I am on wubi ?

-Yos

---

### Post by P4man on 2009-11-01
> **YosefKaro said:**
> Please help, Karmic won't shut down or reboot: I always have to manually press the power button.  Karmic is an upgrade on wubi.  Any suggestions would be appreciated.

Another problem I am having is that on start up, Karmic is saying that my HD is failing: that it has 82 bad sectors...I ran several diagnostic checks and they all report that my HD is in perfect health.  Could this false alarm be caused because I am on wubi ?

-Yos

If palimpsest is reporting a huge amount of relocated sectors, then its a bug you can safely ignore ( you can turn of the warning for that drive until its fixed) 

for the not shutting down, does it do anything at all when you ask it to reboot or shut down?

---

### Post by kaurman on 2009-11-01
Maybe you'll get some more information if you initiate the shutdown from the terminal. The command is 'shutdown -h now'. It must be run as a superuser.

---

### Post by YosefKaro on 2009-11-01
Yes, it does try to shut down, saying that it is trying to shut down processes, etc. but then it hangs until I manually shut it down.

---

### Post by YosefKaro on 2009-11-01
This is what I get when I try to shut down:

*Stopping Kernel Oops catching service kerneloops
*Shutting down ALSA...
*Asking all remaining processes to terminate...
*Deconfiguring network interfaces...
*Deactivating swap...
[    171.180168] Buffer I/O error on device loop0, logical block 3834127
[    171.180116] Buffer I/O error on device loop0, logical block 3856120
_

and there it hangs with a flashing cursor.

---

### Post by P4man on 2009-11-01
Sounds like a regression of this bug:
[https://bugs.launchpad.net/wubi/8.04/+bug/204133](https://bugs.launchpad.net/wubi/8.04/+bug/204133)

Try and update you system.
While waiting for a proper fix, you can probably reboot or shut down your machine nicely using this:
[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

replace the B and the end with O (I think) to shut it down instead of rebooting.

---

### Post by YosefKaro on 2009-11-01
Wow, that really works...Thank you so much :p

Now how do I change this thread to resolved ?

-Yos

---

### Post by P4man on 2009-11-01
> **YosefKaro said:**
> Wow, that really works...Thank you so much :p

Now how do I change this thread to resolved ?

-Yos

In thread tools. But if you are only able to shut it down using magic syskeys is hardly a real solution. More like a workaround.

---

### Post by YosefKaro on 2009-11-01
I'm totally new to ubuntu, the forums, and the community...where would be the best place for me to report this as a problem so that it may be resolved in a future update.

-Yos

---

### Post by P4man on 2009-11-01
> **YosefKaro said:**
> I'm totally new to ubuntu, the forums, and the community...where would be the best place for me to report this as a problem so that it may be resolved in a future update.

-Yos

The link I gave to launchpad above. Thats the place to report bugs. You'll have to sign up first, then add a new comment providing the info you gave here and mention which ubuntu version you are using. You will then also be notified of any changes to the status of the bug.

The forum here is were you can get help from other *users* to help with questions or possibly work around bugs, but to get bugs fixed they need to be reported to the *developers* who check launchpad, but not necessarily the forums here.

Welcome by the way :)

---

### Post by P4man on 2009-11-01
Detailed explanation on how to report bugs can be found here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

But since you are a new user, its best you check here on the forum first so you dont report bugs which arent bugs. Your problem with the failing disk message is a known bug, I dont think its useful to report it again.  The issue with not shutting down I would report as in the bug report I linked I dont see anyone using Karmic (9.10).

---

### Post by poo706 on 2009-11-01
This is getting talked about on all of these other threads:
[http://ubuntuforums.org/showthread.php?t=1306005](http://ubuntuforums.org/showthread.php?t=1306005)
[http://swiss.ubuntuforums.org/showthread.php?p=8206421](http://swiss.ubuntuforums.org/showthread.php?p=8206421)
[http://georgia.ubuntuforums.org/show....php?p=8206461](http://georgia.ubuntuforums.org/show....php?p=8206461)
[http://georgia.ubuntuforums.org/showthread.php?p=8216794](http://georgia.ubuntuforums.org/showthread.php?p=8216794)

So far, P4man's advice regarding REISUB is the best information I've found on this issue so far, and as he said, it's a workaround at best.  I gave it a shot and when I get the buffer errors, I can get it to shutdown without holding the power button, but I couldn't get it to reboot via that method. In doing searches for this nearly every day for the last few weeks, it looks like it's a problem that's hit Wubi before. And there's a lot of people talking about it, so I'm sure a fix will be released soon.

[poo]

---

### Post by blagosphere on 2009-11-07
I have the same shutdown problem.. but get this it will restart. i recently installed it again and it solved my driver error so im happy with karmic overall. i hope to see this fixed soon but thanks for the reisuo workaround!

---

### Post by mattsl on 2009-11-30
I've ran into the same bug. New Karmic install through wubi. Exactly the same behaviour as described by otehrs in this thread. Has someone filed a report yet?

---

