---
title: "Unbuntu 9.10 hangs on dell Latitude d600"
date: 2009-11-16
forum: General Help
---

### Post by gbfoxbat on 2009-11-16
I installed the latest 9.10 on a dell d600 the install part went well its a clean install formatted hd etc... After the install when ubuntu starts up after a few minutes the laptop hangs, this happens also with live cd as well. Any ideas and help appreciated.

Thanks

---

### Post by plusnplus on 2009-11-16
Hi gbfoxbat,
Have you install older ubuntu ver. before in your notebook?
There is possibility the CD(9.10) is not working.

---

### Post by gbfoxbat on 2009-11-16
> **plusnplus said:**
> Hi gbfoxbat,
Have you install older ubuntu ver. before in your notebook?
There is possibility the CD(9.10) is not working.

Nope this is a fresh install didn't have any Ubuntu before. Do you think would make sense to install an older version and then upgrade? If so which version would make sense.

Thanks

---

### Post by PRC09 on 2009-11-16
I have a couple of those and have had no problems when running 9.04,but havent tried 9.10.Your problem sounds more like a hardware issue than software.Check that all the fans are running,heat can cause symptoms such as that.maybe try using 9.04 and see if you still have the same problems.if so then its most likely hardware issue...

---

### Post by gbfoxbat on 2009-11-16
> **PRC09 said:**
> I have a couple of those and have had no problems when running 9.04,but havent tried 9.10.Your problem sounds more like a hardware issue than software.Check that all the fans are running,heat can cause symptoms such as that.maybe try using 9.04 and see if you still have the same problems.if so then its most likely hardware issue...

Well in the mean time I installed Linux Mint on the same laptop and it works. The browser is very slow visually/display and also page scrolling I mean.So probably that has something to do with the display settings. As I understand it Mint uses Ubuntu Kernal.

---

### Post by PRC09 on 2009-11-16
These are all stock machines with the only upgrade being they all have 2gb of ram,so not sure if that is the difference....

---

### Post by hufemj on 2009-11-22
I'm having the same problem on my D600 as well. This is an old work laptop that IT upgraded and forgot to take back. I had no real problems running XP, that is other than the normal XP problems on any piece of HW. I tried doing a fresh install from CD, blowing everything away, and the system does come up, but hangs after a few minutes. I thought it might be the wireless connection so I tried the wired interface. First, it hangs using Firefox. Tried again, this time starting with the update manager. That hung, too.

When the system hangs, there's a circular icon that I think serves the same purpose as the download hour glass. Within the circle, there are two or three dark dots around the inside perimeter and half a dozen or so grayed dots. There's no motion. I think the dots are supposed to alternate between dark and gray to indicate progress. Also, the video shows problems. For example, the update manager dialog box has a normal title bar, but the space immediately below it and above the big display frame is filled with noise instead of text.

---

### Post by PRC09 on 2009-11-22
The only setting I can think of that might make a difference in bios  is on screen 4 of 7 where it asks which video is default and my setting is system vs dock video card.also video expansion is set to enable.Dont know if this will help...

---

### Post by hufemj on 2009-11-24
I decided to try an older version and installed 8.04. That worked with no problems. I would have tried a slightly older version like 9.04, but couldn't find out where to get it.

In any case, it looks like there's a problem with 9.10 on Dell d600 laptops.

---

### Post by SDNick484 on 2009-11-25
I've seen a couple hangs on my brother's D600 as well, both occurring during heavy disk accessing.  The first hang required a reboot, the second I was able to fix by killing X.  I'll look into this more, but this system ran 8.04 without issues.  My brother also mentioned suspend no longer works, which I also plan to look into (again, it was fine on 8.04).

EDIT: I was able to resolve the suspend issue by blacklisting yenta-socket.  I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362920") which refers to the issue and added the fix there as well (I'm NickA there).  As for the hang issues, I added the entries suggested in [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1305349") (particularly post 4) and haven't noticed the issue sense (although I haven't thoroughly tested it).

---

### Post by hufemj on 2009-12-04
> **SDNick484 said:**
> I've seen a couple hangs on my brother's D600 as well, both occurring during heavy disk accessing.  The first hang required a reboot, the second I was able to fix by killing X.  I'll look into this more, but this system ran 8.04 without issues.  My brother also mentioned suspend no longer works, which I also plan to look into (again, it was fine on 8.04).

EDIT: I was able to resolve the suspend issue by blacklisting yenta-socket.  I found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362920") which refers to the issue and added the fix there as well (I'm NickA there).  As for the hang issues, I added the entries suggested in [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1305349") (particularly post 4) and haven't noticed the issue sense (although I haven't thoroughly tested it).

This tip worked great. I have a D600 that hung with 9.10 and went back to 8.04, because that was the only previous release I could find in five minutes of digging around on the ubuntu site. I had no problems with 8.04. It took me awhile to figure out how to upgrade from 8.04 because the 'upgrade' button did not show in the software updates dialog box. A tutorial in ubuntugeeks showed how to change that through System->Administration->Software Sources->Updates(tab)->Release Upgrade, setting it to Normal Releases. From there I stepped upgraded to 8.10. No problems. Upgraded to 9.04. No problems. Upgraded to 9.10. Problems. The tips suggested in the link above fixed the problem.

There was one more thing to do. While the system was now usable, the display was flaky - slow, needed refreshing, and so forth. The problem was the ATI driver. The driver needed to be removed. See [http://ubuntuguide.net/how-to-fix-screen-mess-after-upgrade-to-ubuntu-910karmic](http://ubuntuguide.net/how-to-fix-screen-mess-after-upgrade-to-ubuntu-910karmic) for the solution. Once the driver was removed (none had to be added), things were back to normal (good).


Thanks!

---

