---
title: "Karmic 64bit boot hangs with 4GB in machine."
date: 2010-02-19
forum: General Help
---

### Post by __lonewolf on 2010-02-19
Hello all,
   I did a little bit of searching for an answer on this, but not much luck with what I am seeing.  I also looked in the messages and syslogs, but could not find anything.  Here are the details.

I have Karmic 64 bit installed, originally with 2GB of memory.  The motherboard will take up to 16GB, and I decided to double to 4GB.  When I put in the 4 memory sticks (1GB each) and reboot, it gets past grub2, to the ubuntu "circle" symbol, the screen blacks out and that is it.  No desktop, no further action that I can tell from the box, just a black screen.  The video feed to the monitor, from what I get with the power light is gone and no activity on the drive.  

If I take out one of the memory sticks, it boots happily up with 3GB and runs fine.  Put the 4th back in, same behavior.  I tried swapping out the old memory, putting in the 2 new sticks, everything works fine.  Add in the other two (the old ones), the problem shows again.  I thought I might be the last memory slot, so I removed the one from the 3rd slot, works fine.  

All in all, it works fine with 3GB, but hangs on boot with the 4GB.  

Any ideas or ideas about what I can look for in the logs?

Thanks,
Terry

---

### Post by Devastator9 on 2010-02-19
Have you run mem test with all 4 gigs?

---

### Post by egalvan on 2010-02-19
I have a machine that will  not boot with a  pair of Kingston 2MEG sticks...

will boot fine with either one, in either slot...
will boot fine with either one and any other brand of RAM...

but will NOT boot with the pair of Kingston 2Meg sticks...ç

I bought eight pairs, and they all work/fail the same way...

and they work fine in every other machine I have tried them in...

go figure...

some RAM/motherboardss are simply not socialble.. :p

---

### Post by __lonewolf on 2010-02-19
didn't think of that.  I did swap them around, but will execute memtest.  Will post later after it finishes with results.

Thanks

---

### Post by dcstar on 2010-02-20
> **__lonewolf said:**
> Hello all,
   I did a little bit of searching for an answer on this, but not much luck with what I am seeing.  I also looked in the messages and syslogs, but could not find anything.  Here are the details.

I have Karmic 64 bit installed, originally with 2GB of memory.  The motherboard will take up to 16GB, and I decided to double to 4GB.  When I put in the 4 memory sticks (1GB each) and reboot, it gets past grub2, to the ubuntu "circle" symbol, the screen blacks out and that is it.  No desktop, no further action that I can tell from the box, just a black screen.  The video feed to the monitor, from what I get with the power light is gone and no activity on the drive.  
...........
All in all, it works fine with 3GB, but hangs on boot with the 4GB.  

Any ideas or ideas about what I can look for in the logs?


Check **all** advanced BIOS settings for anything that maps memory about 4GB, and see if changing things help.

---

### Post by __lonewolf on 2010-02-20
alright, checked this morning and the memtest said it ran fine and found no errors.  the only strange thing was the two bars at the top one said 97% and I can't remember what the other said.

I looked through the bios and didnt' see anything that dealt with memory at all except two read only lines showing base and full.

The bios is the original bios (2007).  If you think it would help, I can try updating the bios.  There are currently 7 bios updates, though the last is still marked as beta.

Just as a side note, this system has a dual boot, with a separate hard drive (IDE) for windows.  Windows booted up fine with the 4GB.  The drive for ubuntu is on a sata drive, if that makes any difference.

Thanks in advance for the help.

---

### Post by zaphod777 on 2010-02-20
Update the BIOS. I had a server one time in NY office that the remote admin was upgrading from 8GB to 32 GB of RAM and just wouldn't boot and the BIOS upgrade fixed it (It was a VMWARE server thats why so much RAM). Sometimes the motherboard can't handle that much RAM without the update. If you read the change logs on the BIOS updates you will probably see a note saying to fix this issue. 

My Dell XPS1530 laptop could only take 4 GB ram at first but now after BIOS updates it can take up to 8 GB RAM. 

Also check all RAM is the same speed.

---

### Post by __lonewolf on 2010-02-20
YEAH!!!

Updating the bios did the trick.  Did the update in two swipes, since the MB manufacturer said to not do more then a 4 level jump for bios updates.  Did not load the beta...We can wait for that.

Everything is working as it should.  Thank you all.

Terry

---

