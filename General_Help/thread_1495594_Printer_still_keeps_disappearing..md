---
title: "Printer still keeps disappearing."
date: 2010-05-28
forum: General Help
---

### Post by Georgia boy on 2010-05-28
Okay, I'm wondering what's next to try. I've done what is in the following thread:

[http://ubuntuforums.org/showthread.php?p=9368036#post9368036](http://ubuntuforums.org/showthread.php?p=9368036#post9368036)

I've also shut down both printer and PC, disconnected the cable between, and also pulled power cord of printer. Reconnected everything and powered back up. The things I tried in both the thread and the cable bit only worked for one time. Then on the following day it would disappear again. It worked beautifully when I first did the complete install of Lucid last month when it came out for final release. But last weekend it started disappearing and when I do get it to show it seems to be only temporary. Has anyone found a permanent fix for this?
Is there a "hard fix" for this being worked on from the developers? 

All help is greatly appreciated. This is getting to be frustrating to have to do a "sudo service cups start" just to be able to print each time. Granted it's fast and easy but need something that makes it stay instead of having to do this each time. I did both steps in that link and it still goes away. ](*,)](*,)

Have a great day and a wonderful weekend everyone!!!!


Thanks

Tom

---

### Post by slamhound on 2010-05-28
I wonder if it might be related to this upstart bug:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

I noticed this problem when I was having problems with virtualbox (vboxdrv needed to be setup after every reboot).  But I realized that the problem was broader and a lot of services weren't getting started at boot.  After reading the bug report, I looked at my printers and saw that my one printer had disappeared, so it appears that cups was one of the services that was affected.  Just as the bug describes it happened sporadically (not every boot, but most).  And just as you described in the other thread, starting cups manually fixed things until the next reboot. You might be able to check whether this is your problem by checking to see whether other services that are supposed to start are also not starting at boot.

---

### Post by Georgia boy on 2010-05-28
So, it looks to me that they have the "Cups Bug" moved from medium to high. Hopefully they will come out with a fix and put into an update for us. I know by reading in the forums that it's not just happening to HP printers, that others are affected also. So, guess I'll just keep an eye on it and if I want to print something and it's disappeared then do a manually cups start by sudo again to print like I had to do this morning.
 Just hope that it happens soon. Gets to be madding at times don't it?

Thanks

Tom

---

### Post by Ithiel on 2010-06-17
This should work:

sudo nano /etc/rc.local

before the word "exit 0", insert the following line:

service cups restart

and save the file by using Ctrl + x.

---

