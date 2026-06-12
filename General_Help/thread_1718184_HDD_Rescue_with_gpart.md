---
title: "HDD Rescue with gpart"
date: 2011-03-30
forum: General Help
---

### Post by GuiGuy on 2011-03-30
I've have a 2T ext4 HDD I need to rescue. I'm reasonably confident that 

sudo gpart -W /dev/corrupteddevice /dev/someotherdevice

will be get me out of trouble. Question; using gpart does "someotherdevice" also have to ext4 or can I use an NTFS formatted USB HDD?

Thanks

---

### Post by crispy_420 on 2011-03-31
What exactly re you trying to do first of all?

Do you just want data off it? Or make the disc functional again?

---

### Post by GuiGuy on 2011-03-31
> **crispy_420 said:**
> What exactly re you trying to do first of all?

Do you just want data off it? Or make the disc functional again?

Either way, but I'd prefer to try and get the data onto a backup device before attempting gpart -W back to the same device.

Thanks

---

### Post by crispy_420 on 2011-03-31
Since file recovery is your primary goal stop using the drive now. 2T is kind of big so limits ability to imaging the device to work with an image. What kinds of data are you looking to recover (music, software, etc.)?

---

### Post by GuiGuy on 2011-03-31
> **crispy_420 said:**
> Since file recovery is your primary goal stop using the drive now.

I understand that. We also have a 3T device at hand, so fitting whatever data is recovered onto it won't be an issue. 

This is the usual linux ext4 thing, the disk filled to capacity and would no longer mount. I've experienced that several times now. Successive attempts to mount it then seems to corrupt the HDD. Where this has happened to me I've been able to go to a backup. 

IN this case the user (not me) has not backed the drive up. It contains a range of file types from .txt to large compressed backup files and video files. 

There are some files that need to be recovered. From what I am reading this shouldn't be too difficult, so back to the question; using  gpart to attempt recovery does the HDD I would write to need to be ext4 also?

Or are the tools that can attempt file by file recovery indifferent to the format of the device data will be written out to? Are there linux equivalents for such things as EasyRecovery on Windows?

NB: I'm thinking of getting [this]("http://www.stellarinfo.com/linux-data-recovery.htm"). Anyone have comments or experience with it?


Thanks

---

### Post by GuiGuy on 2011-03-31
Nevermind, there is a free (trial?) download of the STellar Phoenix software. I'm running it now and it does seem impressively simple yet competent.  It's got an hour or so to go. I'll report back.

Update: Ahemm.... it has a day or so to go.... :P

Cheers

---

### Post by crispy_420 on 2011-03-31
That much data will take forever. But my solution would have been to create a DD image of the drive to work on file carving. Then use tools such as foremost and photorec to recover any data recoverable. The good thing about a DD image is that you can't accidentally write a bit to drive and corrupt the data.

Good luck with your solution and hopefully you can flag this thread as solved soon.

---

### Post by GuiGuy on 2011-04-01
> **crispy_420 said:**
> That much data will take forever. 

Time's not an issue. 


> But my solution would have been to create a DD image of the drive to work on file carving. Then use tools such as foremost and photorec to recover any data recoverable. The good thing about a DD image is that you can't accidentally write a bit to drive and corrupt the data.

I'm somewhat naive about ext4 data recovery. I started reading up on it but I think to come to terms with it would take longer than what Stellar Phoenix is doing now; 12 hours in it's about half way done. 

> Good luck with your solution and hopefully you can flag this thread as solved soon.

Will do. Thanks for the input.

---

### Post by GuiGuy on 2011-04-01
Stellar Phoenix proved useless. 
BUt it's all good! Where everything came up blank, [ Raise Data Recovery from SYSDEV Laboratories]("http://www.ufsexplorer.com/rdr_ext23.php") saved the day. Brilliantly easy to use, amazingly fast compared to the linux solutions I have tried, and it seems to be recovering everything.

---

