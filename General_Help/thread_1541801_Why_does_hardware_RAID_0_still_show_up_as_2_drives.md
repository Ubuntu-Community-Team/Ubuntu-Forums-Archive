---
title: "Why does hardware RAID 0 still show up as 2 drives?"
date: 2010-07-29
forum: General Help
---

### Post by lumix on 2010-07-29
I have two 400 GB drives set up in my Fastbuild utility (HP on-motherboard sata-RAID) as LD 2-1 and LD 2-2 at RAID level 0.  I also have LD 1 set up with a 250 GB drive in JBOD.  So I expected linux to know nothing about the 2 400G drives and simply report 2 drives total: 1 250G and 1 800G.  But it apparently wasn't fooled.

Why is this?

---

### Post by prodigy_ on 2010-07-29
What you have is probably a so-called fakeraid, not a true hardware raid. Since it's only partially implemented in hardware, Linux sees its member disks.

The question is, does Linux also see the 800GB raid device? If this device is present and you can partition it, then there's nothing wrong.

---

### Post by lumix on 2010-07-29
Thanks for the reply.  

fdisk -l shows no such (800G) device.  Should I be looking somewhere else?

---

### Post by prodigy_ on 2010-07-29
From my experience, **fdisk** doesn't understand fakeraid devices. Use ```
sudo parted -l
``` or Disk Utility (System/Administration/Disk Utility) instead.

---

### Post by pricetech on 2010-07-29
I ran into the same thing, only mine was a Dell.  You can still do software RAID if you're so inclined, but you'll have to use the Alternate CD.

---

### Post by john newbuntu on 2010-07-30
If you fire up gparted, on the top right corner, you will get a list of disks.  Choose the /dev/mapper/* if it is available and that will give you your fakeraid details.
Vanilla fdisk -l just reports about individual drives and ignores fakeraid/sataraid.

You could run "sudo dmraid -s" to list your fakeraid name and then use the name in fdisk.  For example "sudo fdisk -l /dev/mapper/nvidia_fdfaeie" assuming nvideia_fdfaeie to be the fakeraid name.

---

### Post by v1ad on 2010-07-30
its a real pain to install linux on fake raid. what you need to do is partition and install without grub and then install grub afterwards. 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lumix on 2010-07-30
Man, what a noob I am.  Always wondered what fakeraid meant.  Kind of a disappointment, but still kind of handy too, I suppose, if it provides RAID transparency at the drive level.

Unfortunately for me I'm working with a CLI only ubuntu at the moment (not exactly Ubuntu then, is it?), so no gparted or disk utility for me.

Thanks for the info.

---

### Post by dcstar on 2010-07-31
> **lumix said:**
> I have two 400 GB drives set up in my Fastbuild utility (HP on-motherboard sata-RAID) as LD 2-1 and LD 2-2 at RAID level 0.
........

You are aware that if **either** of these drives fail you will **lose all data on both drives**?

---

