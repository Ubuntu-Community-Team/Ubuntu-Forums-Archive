---
title: "Installation woes...first-time user, 10.04 Desktop (64bit)"
date: 2010-11-23
forum: General Help
---

### Post by Fixee on 2010-11-23
I have a custom-built machine:

Pentium i7 930 (8 cores)
6GB RAM
Nvidia 925 GTX
3x 1TB SATA disks
Cisco WUSB100 Wireless adapter

I had Windows on it... worked fine.  Wanted to see what all the excitement was about wrt Ubuntu (I have used console-based Unix for 25 yrs off/on).

Tried 10.10 Desktop and spent 2 days unable to get it to work.  (It istalled fine, but was having system lag, probably due to some contention between GPUs and CPUs (this is well-documented on these forums; I tried diff kernels, video settings, disabling compositing, finally gave up like many others did).)

So now I'm trying 10.04 Desktop, 64-bit.  Boots fine from LiveCD, though can't get the network up.  I partitioned first drive with 18GB swap, the rest as ext4 with / mounted there.  The other two disks are ext4 with /home and /usr respectively.  The rest of the install was completely standard.  Install finishes, says "just reboot" and I do.

I get kernel panic, out of memory after about 30 secs of waiting.  BIOS settings are normal, no GRUB menu even appears, and ESC doesn't summon it.

I'm new to Ubuntu and have no idea how to proceed from here.  It's hard to debug without even being able to get a root shell.  I'm willing to try other kernels, but unsure how to get them installed without even a base system running.  The LiveCD version seems to be unable to access the HDs as far as I can tell.

Any help gratefully accepted.  Huge thanks to all Ubuntu developers and forum supporters for making quality software available to all... for free.  Wow.

---

### Post by Swagman on 2010-11-23
Nvidia 925 GTX

**925** ????

Wow.. How much did that cost ?

---

### Post by sikander3786 on 2010-11-23
Hi. Welcome to the forums and Welcome to Ubuntu :popcorn:

> I partitioned first drive with 18GB swap

I suggest that is too much space for swap on any machine. It won't hurt but you can reduce that space to regain it for regular use.

> no GRUB menu even appears, and ESC doesn't summon it.

Ubuntu is using Grub2 and to trigger the menu, you need to press and hold down Shift key at Bios screen.

> I get kernel panic, out of memory after about 30 secs of waiting

Can you please list the error found there?

---

### Post by Fixee on 2010-11-23
> **Swagman said:**
> Nvidia 925 GTX

**925** ????

Wow.. How much did that cost ?
I had to turn both of my kids over to Nvidia.  And I still owe them another kid, if I can manage to impregnate my wife one more time.

Ok, I typo'ed 295. ><

---

### Post by Swagman on 2010-11-23
lol

Your description probably is correct though !!

---

### Post by Fixee on 2010-11-23
> **sikander3786 said:**
> Hi. Welcome to the forums and Welcome to Ubuntu :popcorn:



I suggest that is too much space for swap on any machine. It won't hurt but you can reduce that space to regain it for regular use.
I agree that's too much.  It was the default and I was too impatient to sit through a repartition.  I have 3 TB of disk and I'm not too worried about 10GB of extra swap.

> 
Ubuntu is using Grub2 and to trigger the menu, you need to press and hold down Shift key at Bios screen.

GAH!!  How did I miss that?!  Thank you.  I googled for GRUB menu hotkey and saw "ESC" about 20 times, but didn't think that Ubuntu might be using a more recent boot loader.

This works, and brings up GRUB with options for a 2.6.35-22-generic kernel (which crashes) and a 2.6.32.24-generic (which simply hangs, but recovery mode works).



> 
Can you please list the error found there? 
I'm going to work for a bit trying to debug the system now that I have a root shell (with the older kernel).  Cheers for the note, and I'll report back here if I get stymied again.

---

### Post by sikander3786 on 2010-11-23
> I'm going to work for a bit trying to debug the system now that I have a root shell (with the older kernel).

You are a hardcore Unix user so you have the right to do that ;-). Let us know of any progress.

Good Luck!

---

