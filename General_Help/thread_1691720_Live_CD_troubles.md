---
title: "Live CD troubles"
date: 2011-02-20
forum: General Help
---

### Post by geerjm on 2011-02-20
OK, so I must preface this with what I've been trying to do and my Linux background:
I am trying to use a live cd to format my primary hard drive. I want XP off for a clean reinstall and then I want to dual boot with 10.10. In the past, on this very machine even, I've successfully used Ubuntu 8.04. 

The problem:
I cannot go beyond the load screen (I believe the Windows screen name which is equivalent is the splash screen). It'll give me the Ubuntu name and the dots that change color....and nothing more than that. I even left it running all night last night, just to see if it was my patience that was keeping this from working. I also have tried the latest Linux Mint just to see if it was an Ubuntu thing. Same result. 

Since the last time Ubuntu worked on this machine (8.04 around two years ago), I have made NO hardware changes. I've scoured the web and forums to no change in luck. But here's what I've tried:

Using nomodeset (after pressing F6 during boot)
Using nomodeset while typing this at the end of command line: i915.modset=0 xforcevesa
Rolling back the video driver in XP
Colorful language


I've received errors occasionally, one of which I wrote down (with the X's denoting numbers that scrolled and changed)
[ xxx.xxxxx] net eth0: (xxxxx) System Error occurred 0

I do not have a clue what that means. 

As for what I am running it on:
Intel P4 2.53 ghz
512 mb ram
Ami Bios 1.21.12
Nvidia GeForce 5200

---

### Post by sikander3786 on 2011-02-20
Welcome to the forums :-)

First of all, I would recommend to check your downloaded image for any defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums are ok, check your disk for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If you need to re-burn the disc, burn at the lowest possible speed preferrably 4x.

That said, you might need to put in some other boot parameter like acpi=off or noapic. There are 6 of them under the F6 menu and any of them might work for you so try them one-by-one. Some more info here.

[http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html](http://ubuntu4beginners.blogspot.com/2011/02/common-installation-problems-with.html)

---

### Post by Quackers on 2011-02-20
Or just nomodeset - not i915 version

---

