---
title: "Unable to mount or remove Disk/volume"
date: 2011-08-28
forum: General Help
---

### Post by Disinform on 2011-08-28
Hi, I'm just getting set up using Ubuntu and wanted to install an LVM drive as a users partition.

I've (somehow - I think possibly while trying to auto-mount the drive on boot with Storage Device Manager) now got to the state where I am unable to mount, format or remove the drive from the volume I have put it in (Users) and every command on the internet I try fails (says the drive is in use).

LVM gives the state of the drive as "Running" but it is unmounted.

Is there any way to force removal of the drive and LVM device and just start from scratch?

(Running Ubuntu 11.04)

---

### Post by kartabosh on 2011-08-28
> **Disinform said:**
> Hi, I'm just getting set up using Ubuntu and wanted to install an LVM drive as a users partition.

I've (somehow - I think possibly while trying to auto-mount the drive on boot with Storage Device Manager) now got to the state where I am unable to mount, format or remove the drive from the volume I have put it in (Users) and every command on the internet I try fails (says the drive is in use).

LVM gives the state of the drive as "Running" but it is unmounted.

Is there any way to force removal of the drive and LVM device and just start from scratch?

(Running Ubuntu 11.04)

did you try umounting it from gparted? 
also, are you sure you are not running any process from that drive?

---

### Post by Disinform on 2011-08-28
I was using Disk Utility, using gparted allowed me to delete the partition but gave an error:

"Changes have been written but we have been unable to inform the kernel about the change [...] reboot."

On reboot it looked good but on re-partitioning the LVM Users re-appeared and everything was locked again.  Seems there's some kind of link I need to break?

There shouldn't be anything running (or even present) on the drive - how would I check?

And thanks for the help.  1.8TB of wasted space is annoying.

---

### Post by Disinform on 2011-08-28
Thanks!

Gparted did it somehow, I kept dismantling the VG partitions and got out of the other side - all now seems good!

Thanks again.

---

