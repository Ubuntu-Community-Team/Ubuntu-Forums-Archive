---
title: "progressive deterioration of ubuntu"
date: 2011-10-02
forum: General Help
---

### Post by tech7 on 2011-10-02
I'm using Ubuntu 10.04 32-bit on a dell latitude d600 laptop.  I've been having serious wifi card firmware issues and recently had to reinstall the OS (again) not even a week ago.  Recently, I've been having this issue where my computer just randomly freezes (i know there's a lengthy unsolved thread open for this, but hear me through).  The freeze has been getting more and more and more frequent.  To the point that everytime I boot up this computer it now freezes at some point, before I'm done using it.
There is no recovering from these freezes, I have to hold power to shutdown.
Only now, it has progressed to the point that I am having a hard time even getting the OS to boot back up.  It will stop loading shortly after posting.  The few times that I can get the OS to boot, none of my firmware drivers are present.  It seems like my current install is progressively deteriorating.

I use this computer all the time.  I code on this computer and having it freeze while I am in the middle of working something through is plain terrible.

I have spent much more time in the last two weeks trying to keep ubuntu working than I have working on the projects that would likely be almost done with had it not been for the issues.

I buy my laptops based on compatability/features and typically buy at least two models at a time; one for writing code in compiled languages (windows xp for using visual studio, etc) and one for web development (ubuntu laptop for lamp and better environment for web coding).  I gave up my previous model due to hardware breakage and moved on to this model because of dependable hardware.  I use Debian and windows xp on my desktop computers.  But, installing/configuring debian to my needs on laptops takes me at least a few hours and won't work with the bcm4306 rev2 wifi card that I currently have.

What I am wondering, should I try to fix this?  Or should I just hock this laptop and try to find another model and OS.  I'm wanting honest opinions here.  I know there are a lot of people here who know Ubuntu and the canonical situation a lot better than I do.  You all have been using this OS longer than I have (2 years) and I've already seen a change in the community and dependability of Ubuntu.  Since I've been spending so much more time trying to work out Ubuntu on my laptops than actually using the OS for what I need it for, I'm really wondering if this issue is worth my time. 

What would you guys do if you were in my shoes?  :confused:

Thanks to any honest replies.

---

### Post by Idefix82 on 2011-10-02
Have you tested the hard drive? Your problem could have a very simple solution, replacing the hard drive.

---

### Post by 2F4U on 2011-10-03
I assume that you already checked the system logs for any suspicous messages that can be connected to the freezes.
If you get random errors or freezes it is often a good idea to test the RAM. Almost any liveCD has an option to run a memtest. Let it run through all the tests even if that takes some time.
And if all that doesn't help and if you don't have the time for further investigation I would look for an alternative Linux distribution.

---

### Post by 3rdalbum on 2011-10-03
Sounds exactly like bad RAM to me; that also explains the more frequent freezing as time goes on.

I found that running a memory benchmark in Phoronix Test Suite caused the crash straight away, every time; which told me that one of my RAM sticks was faulty.

If you can access the RAM on your laptop, try taking out one RAM stick and seeing if that helps. If the problem persists, put that stick back in and take out the other one.

---

### Post by tech7 on 2011-10-03
hmm, you know; the ram issue really made me perk up.  Made all the sense in the world to me after I had read that.  So, today I replaced both of the ram cards with brand-spankin' new cards.  A boot or two later; totally tanked just like before.  

> Have you tested the hard drive? Your problem could have a very simple solution, replacing the hard drive.
Idefix82, thanks for the suggestion.  Seems like I had done that when I had initially received the computer.  But, when I get home in the morning, I'll bust out some of my boot-usb's and give that another shot.  Not a bad idea atall.

---

