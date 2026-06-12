---
title: "USB startup disk creator format my WD HD 1 TB"
date: 2010-03-07
forum: General Help
---

### Post by raulricardo21 on 2010-03-07
Greeting.

Please, be kind about my english.

As the title say, I was formatting a USB genius 2 GB for USB booting ubuntu, but at the first time didn't work, so select that usb and push the option format happen...  The program damage my external hard disk brand Western Digital of 1 TB and 3 partition of that disk.

I'm deeply sad and hopeless... googling a little bit  I found that this is and old problem, was my first try... :cry::cry::cry:

I have a lot, of very important information, I'm so sorry, I don't even know if is this the right group on this forum to put my question.

But a little hope tell me that the information still there.

I'm begging you, please help to rescue my disk... I'm so shocked I don't know where to start... please, help me... I implore you, give me a light in this issue

---

### Post by darolu on 2010-03-07
This link may help you: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by raulricardo21 on 2010-03-09
Hi again, thanks darolu for your quick response.

I'm a little bit calm now, but I'm still really sad, I know that does not help. So here I want to check again, what I want.

In first place I want to show you a couple of screenshot of my hard disk.
[ATTACH]149561[/ATTACH]
[ATTACH]149562[/ATTACH]

And a screenshot of gparted.
[ATTACH]149563[/ATTACH]

So I don't want to waste your time with my sentimental appreciation of the present condition of my hard drive.

The facts are, already say it, but once again summarized:

[LIST=1]
[*]USB Startup Disk Creator (usb-creator) with his buggy as a hell button, format my HD western digital 1 TB.
[*]How usb-creator does that format. I don't know, but for sure, I seriously doubt, for the behavior that the program had actually been able to delete any information. Or at least do not do a srly delete. or maybe I'm too noob to understand what really mean format :D
[*]
What was in my HD? 3 similar sized partitions, ext4, ext3, ntfs in that order.
[*] I did not try ANYTHING on that.. till I know what to do.
[/LIST]

Now, here my questions and desires.

[LIST=1]
[*] I really want to recover as much as possible, but I need to be sure what to do.
[*]Maybe, there is a way to restore the type of partions and recover all my file with a few commands? (too naive?)
[*] If I try to use a recovery too like testdisk, should I preformat my hard drive. Or work in the actual status.
[*] one of that 3 partition, that ext3 one, did haven't so valuable information, if I do that portion of disk ext3 again, can I use that space for recovery?
[*] Should I resign, and start over again my life.
[*] My english is too bad and you don't understand a damn thing ](*,)

[/LIST]

Thanks again, I know you do your best effort with every answer, I really appreciate that....

---

### Post by em3raldxiii on 2011-04-09
Wow, this handy little application is *very* dangerous!  I can completely understand the OP's concern.  I am by no means new to linux or ubuntu, or computing in general, so for this problem to occur to *me* makes me shudder to think what could happen to many other folx.

Quick synopsis:  

1. Downloading the latest Ubuntu.  Want to put it on a USB stick to demonstrate to friends & clients.  

2. Follow instructions on Ubuntu's download page following the "show me how" link.  

3. Select my USB stick from the "USB Startup Disk Creator", click format.  Error, can't find volume.  

4. I click on the top item in the list (as that is where the usb stick had been), and hit format again.  

5. Oops!  That's my 2TB external HD!  Click cancel - but it's not clickable!  Close the program!!  Not responding! Force quit!

6. Open Disk Utility.  What the heck?  It's currently working on formatting the drive (Fat32 of all things!!)  CANCEL!!!!

7. Open a file browser (nautilus of course), click on 2000GB Filesystem.  Doesn't mount.

8. Anger, mashing of keys, thumping of desk, pulling of hair.  Finally, exhausted, I ask the ceiling, "Why?"

LOL!  Luckily I have everything backed up.  It's just a severe pain in the rump.  This kind of problem *MUST NOT EVER EVER EVER OCCUR!* At the very least, a window should pop up, "Are you sure you want to erase your entire 2000GB drive?"  Honesty.

---

### Post by garvinrick4 on 2011-04-09
The one I have heard of the most is in Linux and using a live cd (install cd using Try Ubuntu)
with internet connection open a terminal and install testdisk:
```
sudo apt-get install testdisk
```
```
testdisk
```
follow instructions given:
##Sure there are some articles by Googling or some user might come along and give you
a blow by blow instruction. But the instructions are given as you proceed in testdisk.

---

### Post by garvinrick4 on 2011-04-09
> The program damage my external hard disk brand Western Digital of 1 TB and 3 partition of that disk.I am sure you can format it and it will be fine you just told the app startup disk creator to do that by selecting the wrong device, a user error. I understand first you want to try to recover your personals but the program just did what you told it to do, must be careful when you are using partitioning tools of any kind. Tough way to learn though. Hope you recover.

---

### Post by garvinrick4 on 2011-04-09
> If I try to use a recovery too like testdisk, should I preformat my hard drive. Or work in the actual status.
Just like it is do as previous post recommends good luck.

---

