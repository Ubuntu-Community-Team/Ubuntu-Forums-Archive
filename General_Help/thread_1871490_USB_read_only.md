---
title: "USB read only?"
date: 2011-10-29
forum: General Help
---

### Post by chasej on 2011-10-29
Hey guys,

I am trying to install a newer version of Ubuntu onto my netbook. I have downloaded the .iso file, and go to system -> administration -> start up disk creator. When I select the .iso and my USB, I get the error:

> 
An uncaught exception was raised:
[Errno 30] Read-only file system: '/media/FLASHDRIVE/.disk


Does anyone know if I can format my USB or is there another way to install Ubuntu onto my netbook (no CD drive).

Thanks,
Chase

---

### Post by lightwarrior on 2011-10-29
There are some USBs that have two partitions.
The SanDisk Cruzer is one of them.
On one partition, it has some fixed software programs (utilities for Windows), it behaves as a CD-ROM disk.

Try installing in the other partition, the other is bigger and writable.

---

### Post by chasej on 2011-10-29
I tried that and it immediately said Installation failed.  I assume it's worth noting that the second partition that you speak of has no value listed under "Free Space" while the other partition that gives the error quoted above has "7.6" listed under "Free Space".

Is there a command that I can change the ownership of my USB drive to user or something in order to just tell my USB drive to Read and Write in the properties tab?

I am a complete newbie.

Thanks for the any help,
Chase

---

### Post by critin on 2011-10-29
> **chasej said:**
> Hey guys,

I am trying to install a newer version of Ubuntu onto my netbook. I have downloaded the .iso file, and go to system -> administration -> start up disk creator. When I select the .iso and my USB, I get the error:



Does anyone know if I can format my USB or is there another way to install Ubuntu onto my netbook (no CD drive).

Thanks,
Chase

I've used the disk creator a few times but my usb was always already formatted.  Does the creator ask you if you want to format it, if so, yes- format and then install the image.   To Fat 32.

---

### Post by chasej on 2011-10-29
> **critin said:**
> I've used the disk creator a few times but my usb was always already formatted.  Does the creator ask you if you want to format it, if so, yes- format and then install the image.   To Fat 32.

The creator does not prompt me to format, so is there a way to format it elsewhere?

---

### Post by critin on 2011-10-29
I'm thinking usb pen drive, and upon reading your second post, I believe you're working with an external usb, right?  Where you're installing it to remain there?   I haven't worked with those.

---

### Post by chasej on 2011-10-29
Well what I want to do is "burn" the .iso to my USB to boot up 11.10 and install it onto my netbook.

---

### Post by critin on 2011-10-29
I work with another (windows) comp, and usually format my pen drives by plugging them in and choosing format in the 'computer' disk area.  Then I install the iso's wherever they happen to be.  I've used the ubuntu creator a couple of times but the flash was already formatted.  Do you happen to know what it's formatted to?  I have no idea why you're getting the error, it sounds like you know what you're doing.

If you have unetbootin, why not plug the usb in, open unetbootin and browse for the image.  I know it will format.

---

### Post by chasej on 2011-10-29
Not sure what it was formatted to, but I just got done formatting it to FAT32, and now after running the creator, I get Installation failed error immediately after... 

Any ideas?

---

### Post by critin on 2011-10-29
If you can't use netbootin, erase the usb and try loading it again.

---

### Post by critin on 2011-10-29
No, it always worked for me--sorry.  If you have another computer, download netbootin and give it a try.  It's never failed me either.  As long as the image is good.  You may need to download another copy.

---

