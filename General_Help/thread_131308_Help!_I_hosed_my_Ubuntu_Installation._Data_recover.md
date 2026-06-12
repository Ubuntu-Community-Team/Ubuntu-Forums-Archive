---
title: "Help! I hosed my Ubuntu Installation. Data recovery needed for 2nd drive."
date: 2006-02-16
forum: General Help
---

### Post by Zeroangel on 2006-02-16
OK, I somehow ended up hosing my Ubuntu Installation. I formatted my secondary HD, and edited /etc/fstab to compensate for the changes to my second HD (i'm 99% sure I used the right syntax). But when I rebooted I got a 'DISK ERROR' message prompting me to insert a working hard disk.

So anyways I went into the ubuntu installer. No option to invoke GRUB to restore my OS to its operational state, so I went into the shell (/boot/grub) and tried swapping my *10* kernel files with the *9* ones hoping it would help. No go.

So I figured that I would reinstall Ubuntu since I have all of my /home/ data on the second HD. Success! However now Ubuntu is not detecting any data on my second HD. Says that it's all one big empty partition.

------------------------------------------
This is what my slave HD looked like before:

[ hdb1(mandrake): ~2.5gb ] [ swap: ~300mb ] [ extended.part [ hdb5: ~1.5gb ]]

After using gparted to partition the drives it looked more like:

[ ~10MB buffer [ extended.part [ hdb6 (empty ext3): ~3gb ] [ hdb5: ~1.5gb ] ]

Basically, I erased the mandrake partition, resized the extended (unmountable container) partition and inserted a new one. I was reading and writing data off of both of these partitions before I restarted the machine and all hell broke loose.
-------------------------------------------------------------------
But now, I am at the dilemma where it sees the hard drive as:
[ ~4.5GB Unformatted ]

Does anyone have a clue on how I can restore these partitions?

---

### Post by AndyCooll on 2006-02-16
You could try booting up a Live CD, and if you can mount your problem Linux drive you should be able to edit config files and the like from it. That might work.

:cool:

---

### Post by Zeroangel on 2006-02-16
(junk post)

---

### Post by Zeroangel on 2006-02-16
[QUOTE=AndyCooll]You could try booting up a Live CD, and if you can mount your problem Linux drive you should be able to edit config files and the like from it. That might work.

:cool:[/QUOTE]

Thx for answering, but thats all taken care of already. My primary HD is already reformatted and i've reinstalled ubuntu on it. It's just the secondary drive that is making me crazzzzzy. :mad: 

*plays crazy train solo*

---

### Post by j2r7 on 2006-02-16
I think what AndyCooll meant is a bootable linux cd like UbuntuLive, Knoppix, Puppy or F.i.r.e. that might have a dd program or testdisk (partition recovery) program on it.  
I would just boot the CD with just the 2nd drive attached and try and mount it, if you can get that accomplished, it should be possible to recove the data either by FTP to some webspace or USB drive or whatever

---

### Post by Zeroangel on 2006-02-17
Ah, I see what you mean now. While I didn't have a liveCD on hand at that time I do now! I downloaded testdisk via the repositories and managed to recover both of my partitions.

Thanks :KS

---

