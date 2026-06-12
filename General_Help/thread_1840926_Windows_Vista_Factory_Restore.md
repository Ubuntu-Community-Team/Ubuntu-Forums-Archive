---
title: "Windows Vista Factory Restore"
date: 2011-09-08
forum: General Help
---

### Post by DaimyoKirby on 2011-09-08
Hello there.

So I have a bit of a problem (windows vista not working), but I'll ask a question first:

I have Ubuntu installed alongside my Windows Vista; I want to do a factory settings restore to my computer, without a disk, but I'm not sure of the consequences.

If I do a factory settings restore (without a disk), will having Ubuntu installed create problems?

I have a Pavilion dv6700, Windows Vista x32-bit, Ubuntu 10.04.

Let me know if you need any other information.

---

### Post by WorMzy on 2011-09-08
I doubt it. You might want to ask on a Windows forum though.

---

### Post by DaimyoKirby on 2011-09-08
I will, thanks.

---

### Post by wildmanne39 on 2011-09-08
Hi, you have window files like on a d: drive is that correct?

If you do a reset in that manner, vista will take the whole drive I believe and wipe ubuntu out or at the very least you will need to reinstall grub to get the boot menu back, I believe the later will happen, but it has been a long time since I have ran anything but ubuntu.
Thank you

---

### Post by haqking on 2011-09-08
> **DaimyoKirby said:**
> Hello there.

So I have a bit of a problem (windows vista not working), but I'll ask a question first:

I have Ubuntu installed alongside my Windows Vista; I want to do a factory settings restore to my computer, without a disk, but I'm not sure of the consequences.

If I do a factory settings restore (without a disk), will having Ubuntu installed create problems?

I have a Pavilion dv6700, Windows Vista x32-bit, Ubuntu 10.04.

Let me know if you need any other information.


Unlikely.  factory resets are usually a bit level copy of a compressed image and replaces whatever is on the drive.

Should be fine.....he says with a little trepidation :?:

but yes best directed to a windows forum

---

### Post by DaimyoKirby on 2011-09-08
Does anyone know a good windows forum to use?

I registered at fourms.windowsforum.org, but I couldn't post anywhere for some reason...

---

### Post by haqking on 2011-09-08
> **DaimyoKirby said:**
> Does anyone know a good windows forum to use?

I registered at fourms.windowsforum.org, but I couldn't post anywhere for some reason...


try here [http://www.vistahelpforum.com/](http://www.vistahelpforum.com/)

but as answered your factory restore will 99.9% wipe everything and put it back to a factory settings....like the title suggest ;-)

good luck

---

### Post by howefield on 2011-09-08
You could try the HP support pages.. eg

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00006110&lc=en&cc=us&dlc=en&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00006110&lc=en&cc=us&dlc=en&product=18703)

---

### Post by haqking on 2011-09-08
> **howefield said:**
> You could try the HP support pages.. eg

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00006110&lc=en&cc=us&dlc=en&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00006110&lc=en&cc=us&dlc=en&product=18703)


+1

ahh yes good point, far better to get support about a factory restore from the manufacturer.

---

### Post by DaimyoKirby on 2011-09-08
But I can't get to where the hp help topic ([http://goo.gl/OInPD]("http://goo.gl/OInPD")) is telling me to go without Ubuntu installed...
And that was why I wasn't sure if I could just go ahead and wipe everything.

Basically, you're all telling me just to go ahead and wipe my computer, as Ubuntu shouldn't affect it at all?

---

### Post by MG&amp;TL on 2011-09-08
Careful...I'm not sure how this works, but do a backup on your files in Ubuntu first. Because on my win 7 laptop, using the inbuilt 'recovery mode' partition deleted something and GRUB refused to function...I don't know if 'factory reset' is the same thing as 'recovery mode' but hey. Caution is a good thing, in my book.

---

### Post by wildmanne39 on 2011-09-08
Hi, the only harm is that ubuntu will be wiped out and you will need to reinstall it.
Thank you

---

### Post by haqking on 2011-09-08
> **DaimyoKirby said:**
> But I can't get to where the hp help topic ([http://goo.gl/OInPD](http://goo.gl/OInPD)) is telling me to go without Ubuntu installed...
And that was why I wasn't sure if I could just go ahead and wipe everything.

Basically, you're all telling me just to go ahead and wipe my computer, as Ubuntu shouldn't affect it at all?


yes you can.

from the page supplied in your link

**Restore the PC to its original condition with the HP Recovery Manager if Windows Vista is not accessible**If  the  PC cannot launch into Windows, it may still be possible to use the  HP Recovery Manager on the hard drive to restore the computer to its  original operating condition. The Recovery Manager can be launched  during the start up process by following the steps below.

[LIST=1]
[*]Press the **Power button**  to start the PC, and then press the f11  key when the standard BIOS prompts are displayed on the black screen.
[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Image/common/note.png[/IMG]
NOTE:Pressing the f11   key during the startup on a computer with an HP factory image will  start the system recovery process even if the prompt is not displayed.
[LIST]
[*]If  the HP Recovery Manager can access the recovery partition on the hard  drive, a prompt to backup the user files before beginning the recovery  is displayed. Follow any on-screen instructions.
[*]If  the HP Recovery Manager cannot access the hard drive to fix any system  errors, you will need to use the personalized  recovery disc that you  created to recover the hard drive to its original condition.
[*]If  you have not created the personalized recovery disc, or the discs are  corrupted, you can order a replacement recovery disc from HP.
[/LIST]
 
[*]When the Recovery Manager starts, follow the [step-by-step recovery instructions]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00809678&lc=en&cc=us&dlc=en&product=18703#RecoverySteps")   shown above.
[/LIST]

**Resolving a common recovery issue.**
If  the original operating system is changed to a non-Vista OS, the  Recovery Manager cannot be launched from either the desktop or by  pressing the f11 key on startup. You can use the recovery disc to  restore the computer to the original operating condition in Vista. If  using an non-Vista OS, you can use a third-party partition manager  program to reclaim the hard drive space.

from this url [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00809678&lc=en&cc=us&dlc=en&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00809678&lc=en&cc=us&dlc=en&product=18703)

This assumes you havent deleted the recovery partition or have the discs to hand ;-)

Remember after this there will only be the factory restore, no UBUNTU will exist anymore

---

### Post by wildmanne39 on 2011-09-08
Hi great directions haqking, also if the recovery drive is still there you should be able to load it by going into the grub menu and choosing vista recovery.
Thank you

---

### Post by DaimyoKirby on 2011-09-18
Thank you everyone!

You'll probably be happy to hear I've completely switched over to Ubuntu after having another problem with Vista (which I've realized is a terrible OS - completely unlike XP and 7):

So I did the factory restore, after copying the files I wanted to keep onto flash drive(s) and another computer. It all went wonderfully, and Vista started up like it was just out of the box. I then started installing updates, and was careful to make sure there was a restore point of the computer in this condition. I restarted my computer to complete a few updates, and got the "Update 3 of 3: 0% error", which seems to be a not-so-unheard-of error with Vista, but that doesn't seem to have a good/easy fix for. So fed up with Vista, and not wanting to have to go through extensive processes that may not even work, I just installed Ubuntu 10.04 from a flash drive and upgraded to 11.04 from there; I've been enjoying have a wonderfully working computer (except for [this]("http://ubuntuforums.org/showthread.php?t=1845700")).

So once again, thank you all for the great advice and help!

---

### Post by wildmanne39 on 2011-09-18
Hi, I am glad you got it sorted out, hopefully you will get the sound working soon.

I have an hp 6000 a few years old I just upgraded it to 10.04, I am not going to install 11.04 on it.
Thank you

---

