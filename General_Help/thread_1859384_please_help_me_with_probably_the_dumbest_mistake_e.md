---
title: "please help me with probably the dumbest mistake ever"
date: 2011-10-13
forum: General Help
---

### Post by Ceipheed on 2011-10-13
So I just DLed 11.10 and I wanted to make a startup USB drive. I got the USB where I had previously tried out 11.04 and  went to the Startup Disk Creator.  

The problem is that I clicked Erase Disk button and authorized it without actually looking at what disk it was gonna wipe and it turns out I wiped out my 1Tb disk.

Yes, I should've checked first and now I know better...](*,)

If there is anything I could do to restore the disk, I'd appreciate your help with it. thanks in advance.

----------edit----------

OK, so I checked again and it turns out it wasn't wiped after all. *haaaahhhhh....*

so, I guess I should delete this threat, but I wonder if I could get some pointers on what to do next time I DO accidentally wipe out a HDD. Good software and any recommendations, if you don't mind.

---

### Post by rbc on 2011-10-13
Depends on your definition of “wipe”. If you mean you wrote zeros to the whole drive, and other random bits, I am afraid you’d be SOL. If you mean you accidentally formatted the drive/partition:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by cryptotheslow on 2011-10-13
If it happened.

1. Stop using the disk immediately. If it is a secondary drive or partition, unmount it to be sure. If it is your primary (root / ) filesystem and you erase with sudo privilege then you won't have much choice in that as the system will essentially hose itself and stop working right before your eyes!

2. Step away from the machine, take a deep breath and don't return until you've stopped panicing. :D

3. Boot up the PC with your LiveCD / USB that you keep to hand for just this kind of disaster. (You do have one right?).

4. If you have another spare drive of sufficient size, take an image / clone of the partition you just erased. This means whatever you do from now on with recovery efforts you have the original image to work with if you make things worse.

5. THINK about what you did. Did you delete a partition (using GParted, parted etc.), or did you delete a whole bunch of files?

6. Deleted files? Mount the partition and carefully have a scout around the Trash - you may have got lucky :D Then start contemplating recovery tools such as photorec.

7. Deleted a partition? Start contemplating recovery tools such as testdisk.

There's testdisk and photorec walkthroughs and tutorials splattered all over the tinterwebs so I do't intend to add another regurgitation of those here. Do some reading :D

If in any doubt about how to proceed - STOP typing that command you "think" will do the job and come here and ask. :D

---

### Post by Vaphell on 2011-10-13
0. if you have anything you can't afford to lose - back the hell up of it! preventing the mess is much easier than fixing the mess.

---

### Post by rbc on 2011-10-13
> Stop using the disk immediately.
If you have another spare drive of sufficient size, take an image / clone of the partition you just erased. This means whatever you do from now on with recovery efforts you have the original image to work with if you make things worse.

Good advice

> Step away from the machine, take a deep breath and don't return until you've stopped panicing. 


Even better advice

 > if you have anything you can't afford to lose - back the hell up of it! preventing the mess is much easier than fixing the mess.

Even better advice

---

### Post by Ceipheed on 2011-10-13
much obliged. I can call it a day with this.

thanks guys.

---

