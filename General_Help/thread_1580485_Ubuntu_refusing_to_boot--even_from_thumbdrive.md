---
title: "Ubuntu refusing to boot--even from thumbdrive"
date: 2010-09-23
forum: General Help
---

### Post by thoenix on 2010-09-23
I have this partner who kept breaking his Windows.  As a Mac user, I got mad and said 'this is it, no more windows in our home!'  So I looked around and looked for some kind of Linux that was an option for him.

Two weeks ago, I loaded Ubuntu 10.04 onto his HP G60.  No major problems for two weeks.  I thought my issues were over!

And now he has broken Ubuntu.  He booted up this morning and accidentally put in the wrong password for our wireless network and then it said wrong password and he put in the right password (he believes, because the 'box went away') and then network icon didn't show up.  He went to go try and open Firefox to see if it was working and hit Places instead of Applications and then it froze.  Then he let it stay frozen for 'a few seconds' and it 'didn't start going again' so he forced it to shut down using the power button.  He turned it back on and then it said 'DNR Error' (this is what he's telling me, I wish he'd just called me when he started having problems).  It would show a 'block of text and then DNR Error again' and it kept showing that over and over so he restarted again using the button.  And then it gave him the internet login when he restarted again and when he put in our password, the box went away and he got a black screen.  After it stayed black for awhile, he forced it to shut down using the power button.

Now when I try to boot up the machine, I'm getting "No init found.  Try passing init= bootarg."

I went online and found that I should run from a startup cd in order to run fsck, so I stuck in my USB that still has Ubuntu ready to go from when I loaded it onto the machine.  

I can get it to talk to the USB, but Ubuntu does not load.  Period.  We're talking ten to fifteen minutes on the purple Ubuntu screen.

Help?  I am WAAAAY out of my depth here.

---

### Post by Rubi1200 on 2010-09-23
What graphics card do you have installed on the machine and how much RAM?

---

### Post by thoenix on 2010-09-23
HA!  Figured out the Graphics Card: NVIDIA GeForce 8200M  And the product specs page for the item says it has "3072 MB of RAM" [Source](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01566904&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=ca&product=3817997&lang=en)

---

### Post by Rubi1200 on 2010-09-23
When you say you > loaded Ubuntu 10.04 onto his HP G60 does that mean you erased the drive and only installed Ubuntu or was this a Wubi install within the operating system?

When you boot the laptop with the USB try following these instructions and see if it helps:
Put the LiveCD (or USB) in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again; (may not be relevant)

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter in this order:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Then Enter to boot

---

### Post by thoenix on 2010-09-23
> **Rubi1200 said:**
> When you say you  does that mean you erased the drive and only installed Ubuntu or was this a Wubi install within the operating system? I said no more Windows, so, afaik, from what I installed, everything else was removed.  Unless I made a mistake, but I don't think I did--an experienced friend was walking me through.

And now, in his epic technology killing, he has killed our cable box!  HE'S JINXED I SAY!  JINXED!

---

### Post by thoenix on 2010-09-23
> **Rubi1200 said:**
> 
When you boot the laptop with the USB try following these instructions and see if it helps:
Put the LiveCD (or USB) in and boot up;

when you see the Ubuntu logo hit Enter; This brings me directly to the purple loading screen, where it will just... stay.  So I can't do any of the rest of what you say.
 

When I hit Enter, some screens of commands or something fly by at speeds that no human being could read and then it goes right to the purple screen and just stays there.

Am I doing something wrong?

---

### Post by thoenix on 2010-09-23
I tried hitting tab instead, seeing that it was an option at the bottom and got this: 
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/pres/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --
```But, as you can see, I don't have the 'quiet' prior to the splash.  Can I attempt what you said from here?

---

### Post by Rubi1200 on 2010-09-23
Are you able to download and put another image on a USB?

Two possibilities:

Ubuntu version 9.10 or the alternate install.
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
(You can find the alternate install image on the same page further down)

Other than that, I am running out of ideas.

---

### Post by Rubi1200 on 2010-09-23
> **thoenix said:**
> I tried hitting tab instead, seeing that it was an option at the bottom and got this: 
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/pres/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --
```But, as you can see, I don't have the 'quiet' prior to the splash.  Can I attempt what you said from here?
Yes, replace splash with nomodeset and then Enter

---

### Post by thoenix on 2010-09-23
Yeah... that didn't work.  I guess I'm gonna try putting 9.10 onto my thumbdrive from my Mac and loading that.  Hopefully THAT works.

He's the epic breaker of electronics.  He's not allowed to touch my Wii or my Mac for a reason!

---

### Post by Rubi1200 on 2010-09-23
Keep us posted and we will try and find a solution for you.

---

### Post by thoenix on 2010-09-23
Will do.

This may be a dumb question, but can I install the 9.10 through a DVD?  So I don't have to remove the 10.04 from my thumbdrive?  And uh... Do I just burn the iso to a disc or do I need to download a program/go through a special program to do it?  I'm sorry to be a total n00b.

---

### Post by Rubi1200 on 2010-09-23
> **thoenix said:**
> Will do.

This may be a dumb question, but can I install the 9.10 through a DVD?  So I don't have to remove the 10.04 from my thumbdrive?  And uh... Do I just burn the iso to a disc or do I need to download a program/go through a special program to do it?  I'm sorry to be a total n00b.
I am fairly certain you can do that. Yes, burn the iso to a disc at the lowest speed possible.

---

### Post by thoenix on 2010-09-23
9.10 seems to be installing!  YAY!  So uh... Now I can't remember how to install Skype... I know there was a terminal command I had to run first on 10.04, but I can't for the life of me remember what it was.  Hopefully I won't need it.  I'm just glad he didn't brick his bloody computer!  Thank you sooooooo much!

---

### Post by Rubi1200 on 2010-09-23
> **thoenix said:**
> 9.10 seems to be installing!  YAY!  So uh... Now I can't remember how to install Skype... I know there was a terminal command I had to run first on 10.04, but I can't for the life of me remember what it was.  Hopefully I won't need it.  I'm just glad he didn't brick his bloody computer!  Thank you sooooooo much!
You are more than welcome :)

Search the forums for Skype, I am sure others have installed it.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

