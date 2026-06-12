---
title: "Increase in ISO size"
date: 2010-07-03
forum: General Help
---

### Post by socrates0 on 2010-07-03
When I downloaded the ISO file thru DAP it showed up as 699.44MB but when I completed the download onto my HDD (XP SP3 & NTFS) it shows up as 716,230KB (see below) with a result when I try to burn on to a CD.  I get an error that the file is too large. Whats happening, is there a solution to this?:(

---

### Post by geirha on 2010-07-03
The size of ubuntu-10.04-desktop-i386.iso is 733419520 bytes = 716230 KiB = 699.44 MiB. Unfortunately Windows incorrectly shows those sizes as KB and MB. See [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix) for more on this madness.

Now anyway, an 80 minute CD can hold about 700 MiB of data, so 699.44 MiB should fit just fine. Though you do need an 80 minute CD or higher (e.g. a DVD can also be used), a 74 minute CD is too small.

---

### Post by socrates0 on 2010-07-04
Thanks for your prompt reply. I was using a 700MB, 80min CD & it did not work, for the last ver I had used a CD from the same box & it had worked just fine. Guess I will now try it with a DVD :)

---

### Post by krishnandu.sarkar on 2010-07-04
If you've downloaded CD ISO then you've to work out a little to burn it on a DVD. You can't easily burn that to a DVD as you would in CD.

I'd say better make a LiveUSB and boot and install from it. Use Unetbootin to create LiveUSB from the ISO image.

---

### Post by socrates0 on 2010-07-04
@krishnandu.sarkar Thanks, I think I will do this to create a LiveUSB and check how well it works on a Compaq Presario V6608AU. [http://ubuntuforums.org/showthread.php?t=1521071](http://ubuntuforums.org/showthread.php?t=1521071). I also want ask a question at the risk of sounding silly, can this pendrive be re formatted to be reused later after I use it as a LiveUSB.

---

### Post by geirha on 2010-07-04
> **krishnandu.sarkar said:**
> If you've downloaded CD ISO then you've to work out a little to burn it on a DVD. You can't easily burn that to a DVD as you would in CD.

I'd say better make a LiveUSB and boot and install from it. Use Unetbootin to create LiveUSB from the ISO image.

Sure you can. Burning the ISO to a DVD is just as easy as writing it to a CD. The procedure is identical.

---

### Post by krishnandu.sarkar on 2010-07-04
> **socrates0 said:**
> @krishnandu.sarkar Thanks, I think I will do this to create a LiveUSB and check how well it works on a Compaq Presario V6608AU. [http://ubuntuforums.org/showthread.php?t=1521071](http://ubuntuforums.org/showthread.php?t=1521071). I also want ask a question at the risk of sounding silly, can this pendrive be re formatted to be reused later after I use it as a LiveUSB.

Of course you can. But make sure to enable USB Boot from BIOS to be able to boot from USB.

> **geirha said:**
> Sure you can. Burning the ISO to a DVD is just as easy as writing it to a CD. The procedure is identical.

Are you sure?? I'm asking this because every time I tried to burn an ISO CD image to DVD it keeps asking me to provide blank CD and doesn't accepts DVD.

Sorry but I just thought LiveUSB would be better because wasting a DVD for mere 800MB is not a good idea. We won't be able to use that huge free space later.

---

### Post by geirha on 2010-07-04
It might be that some programs don't handle it that well, but Brasero sure didn't mind when I burned Lucid earlier this year. I just popped in a recordable DVD (was out of recordable CDs). A window asking me what I wanted to do with it popped up where I answered "do nothing", then I right-clicked the iso and chose burn. Easy.

In terms of space usage, it sure is a waste to only use a small portion of the whole DVD. But now adays, recordable DVDs cost almost the same as recordable CDs, so in that respect, it's not that much of a waste.

If you have a 1G+ USB stick handy, that's of course a good option too.

---

### Post by socrates0 on 2010-07-04
@ geirha & krishnandu.sarkar  	Thanks for giving me your time trying to help a newbie like me. I finally managed to burn the Live CD.I was trying with CDBurnerXP then I shifted to IMGBurn & it worked like a dream.
Thanks once again.:D

---

### Post by krishnandu.sarkar on 2010-07-04
@geirha Hmm...I tried Nero in windows. Never tried that in Brasero or K3B. :)

@socrates0 You are always welcome

---

