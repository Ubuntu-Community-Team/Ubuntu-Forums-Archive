---
title: "Random lock-up and memory unrecognised"
date: 2011-09-15
forum: General Help
---

### Post by asearle on 2011-09-15
Hi Everyone,

I have a Compaq 6910p which runs Linux beautifully (everything works!).  However, I have two problems and am wondering whether they are connected:

First I decided to "max out" the memory and so bought a pack of two compatible memory units giving the unit 4Gb in total.  On boot the system recognised the new modules and I clicked to accept the change.  Next I checked in BIOS and the system registered the 4Gb.  However, when I looked in Ubuntu system monitor, the total was still registered as 2.9 (3 ?) Gb.  I tried all kinds of other combinations and the memory seemed to adjust itself accordingly (i.e. less) but when I put the 4Gb in, Ubuntu only registered 2.9.

Can anyone help me with getting Ubuntu to recognise the memory?

The other issue that I have is that since installing 11.04 the system seems to "lock up" spontaneously at random moments.  When this happens I find that I have to power-down in order to get it going again.  Arrgghh!

This is one reason why I decided to upgrade/replace the memory:  I believed that it might have been an error in a memory module.  But this seems to not be the case.

Other thoughts that I had were that it might be my using VirtualBox (which reserves a lot of memory for Windows sessions) but I have de-installed this and still have the problem.

I also thought it might be the fact that I have now encrypted my home folder(s) (so that data is not accessible if the unit gets stolen) and that maybe the system is struggling with the encryption?

It most often happens when I am am on battery power so I am wondering whether that is the issue (and maybe I just need to live with it?)

I have installed all updates but that also hasn't help.

As you can imagine this is all a real irritation so any tips would be gratefully received.

Regards and thanks,
Alan Searle

Cologne, Germany

---

### Post by mcduck on 2011-09-15
That sounds like you are running 32-bit version of Ubuntu. Try with 64-bit version instead.

32-bit operating systems are only able to address up to 4GB of memory, and that includes all the memory in the system, not just your RAM, so for example if your graphics cards has 1GB of memory the system will only be able to address 3GB of RAM. Also the amount of space the Linux kernel takes in RAM is always deducted from the total available memory value, since you'd never be able to use that part of RAM for anyhting else.

I can't say much about the lockup problem, though, there really isn't enough information to say anyhting for sure. I'd recommend just trying to go through all the various log files and of course paying close attention to whatever youa re doing at the computer when it stalls. Perhaps somebody else has better suggestions what you might try to find out the problem...

---

### Post by asearle on 2011-10-09
I reinstalled the 64bit version (10.04 LTS) and this seems to have fixed the problem:  All my memory is recognised and I haven't had any lock-ups (yet).

Many, many thanks for your help.

Regards,
Alan Searle

---

