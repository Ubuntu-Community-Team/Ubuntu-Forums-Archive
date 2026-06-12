---
title: "Drive mounted as sdb instead of sda and vice versa"
date: 2012-03-26
forum: General Help
---

### Post by dannyvanderzande on 2012-03-26
I am trying to set up a ubuntu server for downloads backups and media sharing.

I installed the system on my 120 GB PATA drive, shut down the system and plugged in a 2000GB SATA drive. Upon checking fdisk for partitioning I found out the SATA drive is now being marked as sda but I want my PATA drive to be sda and the SATA drive to be sdb because I'm used to this setup...

I have googled around but I can't seem to find a proper solution. Everyone keeps talking about this UUID but this'll only work for a partition and not for an entire drive.

Can anyone help me out or give me a pointer in the right direction?

Thanks!

---

### Post by gsgleason on 2012-03-26
Can you tell us why it matters?  

Check the BIOS boot order and the order of the SATA devices in there as well.

---

### Post by Roasted on 2012-03-26
> **gsgleason said:**
> Can you tell us why it matters?  


Hate to say it, but I'd like to question this too. My system has quite a few drives in it, but Ubuntu is on /dev/sdd. Just the way it worked out. I do think it's dependent upon which SATA port the drives are plugged into...

---

### Post by dannyvanderzande on 2012-03-26
I'm used to having my system on /dev/sda and my other files on /dev/sdb... It's just that I like having everything the same so I won't make mistakes when I switch pc's a lot

---

### Post by gsgleason on 2012-03-26
That is why it is recommended to use the filesystem UUIDs for your mount points.  They don't change.

Furthermore, you don't access the block devices directly (/dev/sda, etc).  You access the mount point (a directory), which isn't going to change either.

UNIX-like OSes aren't like windows where you access the devices by a drive designation.

But to answer your question, check the following:

SATA port numbers on the motherboard
BIOS boot order
BIOS SATA drive order

---

### Post by Roasted on 2012-03-26
Yeah... UUID is significantly better for permanent drive mounting than referring to the /dev/sda names. Those names can change simply by moving drives around. UUID doesn't change unless you reformat the drive...

---

### Post by dannyvanderzande on 2012-03-26
@gsgleason thx for your help.
I checked my bios settings. Changed SATA controller to AHCI and after a reboot I was pleased to see my drives were now called how I want them!
Thanks a lot!

---

