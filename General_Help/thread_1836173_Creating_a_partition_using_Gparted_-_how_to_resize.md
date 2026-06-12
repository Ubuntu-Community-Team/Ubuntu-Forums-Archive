---
title: "Creating a partition using Gparted - how to resize root partition?"
date: 2011-08-30
forum: General Help
---

### Post by Potsoil on 2011-08-30
Hi,
I want to reinstall Tiger 10.4 on my mac to use as a backup while I work out some hardware and software issues on Ubuntu.
I've downloaded Gparted, and I want to resize my root partition to make room for a new one. So I need to unmount it to do that - how can I do it if I don't have another operating system also installed to do it from?

There are currently 3 partitions:
/dev/sda1 (!) | Unknown ? 977.00 KiB | --- | --- | bios_grub
/dev/sda2      | ext4| / | 147.08 GiB | 9.37 GiB(used)| 137.71 GiB (unused)
/dev/sda3      | Linux-swap | 1.97 GiB

---

### Post by BlinkinCat on 2011-08-30
I'm no expert, but firstly I think you need to run gparted from a OS CD -

---

### Post by Enigmapond on 2011-08-30
Correct. The volume which you are are trying to re-size has to be un-mounted so the best way is to boot into a live CD and use gparted from there.

---

### Post by Potsoil on 2011-08-30
so I run Tiger from the CD, then resize from there...but will I be able to access the gparted program from Tiger? Or will I need to download a mac OSx partition thing instead?

---

### Post by Enigmapond on 2011-08-30
Eh? You are talking about re-sizing your root in Ubuntu? Can you be a bit more specific? You run Gparted from a live CD to re-size ubuntu....for anything else...please consult a MAC person... :))

---

### Post by Potsoil on 2011-08-30
Well I currently only have Ubuntu 10.4 installed, which has all the hard drive, and I want to install Tiger 10.4. So firstly I need to resize the partition with Ubuntu so I can create a new partition, right?

---

### Post by cryptotheslow on 2011-08-30
Correct. But you cannot resize the Ubuntu partition while you a running that installed version of Ubuntu.

You need to boot the system from a CD or USB device with Ubuntu on it, then use GParted from that version to resize the partition on the hard drive.

Probably the simplest way is to download the ISO file from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and use the instructions linked from that page (step 2) to make a bootable CD or USB from it.

When booting up from the CD or USB take the "Try UBUNTU" rather than the install option! You will be presented with a standard Ubuntu desktop from which you can access GParted and do the necessary to your partition as it will not be mounted.

**NOTE - always backup your files before altering partitions in anyway. GParted is good and personally I've never had a problem with it, but one never knows.**

---

### Post by Potsoil on 2011-08-31
Thanks for the info!
I've resized and created a new partition and am now at the installing Tiger stage...

I know this isn't an apple forum, but when selecting a destination for it to be installed, a hard drive called 'untitled' with ~30Gb space (the amount I chose for the new partition) is the only option, but with a yellow (!), and it says:

```
**The destination disk must be erased for installation.**

The destination volume will be completely erased and a new copy of the Mac OS X installed on the volume. All your data will be lost.

Format as: Mac OS Extended (Journaled)
```Does this mean it's merely erasing the settings on the partition or my whole hard drive? If it's the latter, then is there any way around this?

---

### Post by dino99 on 2011-08-31
> **Potsoil said:**
> Thanks for the info!
I've resized and created a new partition and am now at the installing Tiger stage...

I know this isn't an apple forum, but when selecting a destination for it to be installed, a hard drive called 'untitled' with ~30Gb space (the amount I chose for the new partition) is the only option, but with a yellow (!), and it says:

```
**The destination disk must be erased for installation.**

The destination volume will be completely erased and a new copy of the Mac OS X installed on the volume. All your data will be lost.

Format as: Mac OS Extended (Journaled)
```Does this mean it's merely erasing the settings on the partition or my whole hard drive? If it's the latter, then is there any way around this?

Yes the devs are taking care of users asleep and/or drunk ;)
as said its the "destination" "partition" not meaning "the whole device"
So maybe take time to read doc and use your lovely Ubuntu distro before trying to do something scary and misunderstood.

---

