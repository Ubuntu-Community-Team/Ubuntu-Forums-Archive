---
title: "Live CD won't boot!"
date: 2010-07-02
forum: General Help
---

### Post by d3dhook on 2010-07-02
Hi,

I downloaded the most recent version of Ubuntu (10.04) and burned it to a CD to be used as a live cd. While it attempts to boot during startup, it does not get far. I get a maroon colored screen with a diagram at the bottom that looked like a stick of ram (although it could have been something else, I guess), an equals sign, and then a man in a circle.

After that, it goes to a black screen with a flashing underscore at the top left, until it turns completely black forcing a restart. The monitor has not lost signal.

---

### Post by an0dos on 2010-07-02
> **d3dhook said:**
> Hi,

I downloaded the most recent version of Ubuntu (10.04) and burned it to a CD to be used as a live cd. While it attempts to boot during startup, it does not get far. I get a maroon colored screen with a diagram at the bottom that looked like a stick of ram (although it could have been something else, I guess), an equals sign, and then a man in a circle.

After that, it goes to a black screen with a flashing underscore at the top left, until it turns completely black forcing a restart. The monitor has not lost signal.

When you get to that screen with the maroon colored screen press the ESC key.

Select the option to test your CD for errors. If it passes, select the option to boot with "nomodeset".

---

### Post by d3dhook on 2010-07-02
> **an0dos said:**
> When you get to that screen with the maroon colored screen press the ESC key.

Select the option to test your CD for errors. If it passes, select the option to boot with "nomodeset".
Thanks for the response!

After hitting escape, selecting a language, and going to the checking for defects, it pulls the same stunt. console-esque screen comes up, flashes, disappears and a blank screen stays there permanently.

Any ideas?

---

### Post by QIII on 2010-07-02
Can you give us some specs on your machine?

---

### Post by d3dhook on 2010-07-02
> **QIII said:**
> Can you give us some specs on your machine?

Did you check the md5sum when you downloaded the .iso?

Does it get far enough that you are offered the option to check the disk for errors?
Thanks for the response,


1G Ram
2GHZ dual core 
5400 NVidia
Hard drive is old and starting to corrupt, but this shouldn't be an issue for a live CD?

I checked the MD5Sum, it was the same:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
d044a2a0c8103fc3e5b7e18b0f7de1c8 (my version)
---------------------------

---------------------------
MD5 Check Sums are the same.
---------------------------
OK   
---------------------------



I get as far as going to the maroon screen and selecting the option for checking the disc for "defects." After selecting it, it pauses for a minute and then goes to the console and after more time passes it goes to a black screen indefinitely.

---

### Post by tpow on 2010-07-02
I'm experiencing the same issue, except I already have Ubuntu installed. The problem is every other live CD won't load since I installed Lucid. I've checked the md5sum of the downloads, and they were all good. My boot order has the CD/DVD drive ahead of the hard drive. Any help would be much appreciated.

Computer specs:
hp dv4 laptop
AMD64 processor

---

### Post by d3dhook on 2010-07-02
> **tpow said:**
> I'm experiencing the same issue, except I already have Ubuntu installed. The problem is every other live CD won't load since I installed Lucid. I've checked the md5sum of the downloads, and they were all good. My boot order has the CD/DVD drive ahead of the hard drive. Any help would be much appreciated.

Computer specs:
hp dv4 laptop
AMD64 processor
Although I'm disappointed it doesn't seem to be a quick fix and that you have the problem as well, I'm glad that it's not just me. Thank you for feedback.

Should I 'downgrade' to an older ubuntu? I'm only doing this for data recovery

---

### Post by tpow on 2010-07-02
> **d3dhook said:**
> Although I'm disappointed it doesn't seem to be a quick fix and that you have the problem as well, I'm glad that it's not just me. Thank you for feedback.

Should I 'downgrade' to an older ubuntu? I'm only doing this for data recovery

I don't think the live CD is the issue, since the md5sum checked out. And Lucid Lynx has been a very stable and reliable distro from my experience with it. But if you have a couple extra blank CD's laying around, it can't hurt to try an older version.

---

### Post by an0dos on 2010-07-02
> **d3dhook said:**
> Thanks for the response,

I get as far as going to the maroon screen and selecting the option for checking the disc for "defects." After selecting it, it pauses for a minute and then goes to the console and after more time passes it goes to a black screen indefinitely.

When you are at the maroon screen where you can select options, [B]hit F6.
[/B]
The menu this pops up has a number of options..
Try selecting "nomodeset' and 'nodmraid' then press Esc then enter and  see if it boots.
If it doesn't then repeat the above and select more or other combos  until you find the one that works.

Once you can boot, write down the selection that worked.

Try the live CD to see if all your hardware works. Then post back here with the items from the list above that worked and ask about how to set those for a full install BEFORE you install.

Otherwise you will have the same problem trying to boot from the  hard-drive.
If you have trouble with any hardware post about that as well.

---

### Post by an0dos on 2010-07-02
I had a desktop computer with a geforce 5200fx and it required the 'nomodeset' flag in order to boot 10.04 from the livecd.

---

### Post by d3dhook on 2010-07-02
> **an0dos said:**
> I had a desktop computer with a geforce 5200fx and it required the 'nomodeset' flag in order to boot 10.04 from the livecd.
Ah! That appears to have done it! Thank you!

Combo was the one you said to use: nomodeset and nodmraid.

EDIT: I expected it to go to a GUI, I'm new to linux. It went to a console and asked for a command. Shortcut to getting to GUI?

---

### Post by d3dhook on 2010-07-02
shameless bump

---

### Post by tpow on 2010-07-02
Turns out my issue was with burning the live CD's. You have to burn the image onto the disk, not save the file to it.

---

### Post by an0dos on 2010-07-03
> **d3dhook said:**
> Ah! That appears to have done it! Thank you!

Combo was the one you said to use: nomodeset and nodmraid.

EDIT: I expected it to go to a GUI, I'm new to linux. It went to a console and asked for a command. Shortcut to getting to GUI?

Hmmm... the livecd should automatically launch Gnome. Once you set the above parameters, continue to boot normally, select your language, and click on the option "Try Ubuntu 10.04 LTS". Do you still get only a terminal? If so, type "startx" and press enter.

You may want to burn a second livecd at the lowest possible burn rate in order to verify that this is not a problem caused by a bad burn.

---

