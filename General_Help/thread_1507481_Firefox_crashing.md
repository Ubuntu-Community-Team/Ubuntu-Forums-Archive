---
title: "Firefox crashing"
date: 2010-06-11
forum: General Help
---

### Post by Man_Beach on 2010-06-11
**I'm getting pretty fed up with 10.04 crashing in Firefox, taking me back to the login screen.**

I had to turn off all of my visual effects in System>preferences>appearance to get it 10.04 to work in the first place, but at least everything (apart from Firefox) worked.

I can't view my hotmail messages because it crashes when I click on the message, and various other sites crash as well - seemingly randomly (sometimes a site will crash, sometimes it doesn't). At least I can dual boot into Windows XP to view hotmail.

For information, I have an ATI Radeon RV100 QZ [Radeon 7000/VE] video card. It worked with 8.10 OK and earlier versions of Ubuntu and SuSE and no, I don't have any Firefox extensions loaded.

I mean, 10.04 has been out for quite a while now. Surely I'm not the only person that this is happening to?

It's getting to be a pain in the buttocks.

---

### Post by beckols on 2010-06-11
Do you have the updated version of flash installed?

It's in the Ubuntu Software Center under Canonical Partners.

Also if that doesn't work or you already have it installed, what happens when you go to that site when running firefox in safe-mode?
```

firefox -safe-mode

```

---

### Post by beckols on 2010-06-11
If that doesn't work for you, go ahead and check out this link:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772/comments/29](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772/comments/29)

It is from bugs.launchpad, and it requires you to add a third-party repository, but if you're ok with this, it seems to have fixed this problem for quite a few people.

---

### Post by Man_Beach on 2010-06-11
Latest version of flash is installed.

Tried Firefox in safe mode. I managed to read the hotmail message which caused the crash - but the next message made it crash again.

I'll try the second option over the weekend, see what happens.

---

### Post by Man_Beach on 2010-06-13
Haven't tried the second option yet - been experimenting, but I'm fairly sure that this problem is linked to flash. Using flashblock, I've been unable to repeat the problem with my hotmail account. But it occurs when flashblock is disabled.

Unfortunately, many sites seem to need flash to work properly.

---

### Post by beckols on 2010-06-13
Yea well I'm pretty sure that's what the fix is for - flash problems.  You might want to take a look through the bug report to verify this, though.

---

### Post by Talon2 on 2010-06-13
> **Man_Beach said:**
> 

I mean, 10.04 has been out for quite a while now. Surely I'm not the only person that this is happening to?



I have great news for you.  You are not the only one seeing problems similar to this in 10.04 (32 bit).  I have found a fix.

My problem:  System unstable.  After a period of using Firefox, the system would do one of the following:

- Reboot the desktop
- Firefox would die
- Kernel dump

My system:

- Dell 530n (ultra linux compatible system) (it came preloaded with Ubuntu)
- Video card:  ATI Radeon 4350 (using default open source driver)

The fix:

- [http://www.google.com/chrome](http://www.google.com/chrome)
  (I downloaded and installed the latest 32 bit version of Chrome for Ubuntu.  I haven't had a problem since.  One vital plugin, xMarks, is now available for Chrome so the move was made easy.  It took me a few days to find and learn a few differences in how the browsers work.  Chrome, in my opinion, has now surpassed Firefox as the best overall browser available.  It is very very fast.)

After using Chrome for a week, all I can say about Firefox is that it is slow and broken.

If you try this, let us know how it works out.

Good luck.

---

### Post by Man_Beach on 2010-06-14
Found a simple solution: Installed Google Chrome!

---

### Post by PinchedNerve on 2010-06-14
> **Man_Beach said:**
> Found a simple solution: Installed Google Chrome!

Unfortunately, that seems to be the only real fix.  Maybe if enough [people complain]("http://ubuntuforums.org/showthread.php?t=1509625") it will get fixed?

---

### Post by Rumpletumbler on 2010-06-25
I've used Firefox for years on both Windows and Linux and never had an issue until the last month and Firefox is crashing fairly frequently.

I've installed Chrome and while I don't care for the look of it so much out of the box (haven't had time to customize) the speed difference is huge on my old slow box. Unless something comes up I don't like a lot I guess I'll stay with Chrome for a while.

---

