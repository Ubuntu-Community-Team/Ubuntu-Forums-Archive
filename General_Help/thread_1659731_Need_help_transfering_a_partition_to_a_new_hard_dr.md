---
title: "Need help transfering a partition to a new hard drive"
date: 2011-01-04
forum: General Help
---

### Post by slgtheindividual on 2011-01-04
I have just put a new hard drive into my laptop (new drive is dev/sdb) I have formatted the new drive as an ext3 system. On my old hard drive I'm dual booting windows 7 and ubuntu, so my old drive (dev/sda) has several partitions. I am trying to copy ubuntu which is on dev/sda3 (which is itself an "extended" file system composed of sda5 "ext3" and sda6 "linux swap") to dev/sdb. Once copied i intend for the new drive to be an exclusive ubuntu drive and the old drive an exclusive windows 7 drive (by getting rid of dev/sda3 whose content should now be on dev/sdb.)
Ubuntu was installed on the old hard drive after windows 7.
I understand the boot loader will be affected although I'm unsure how.
I have Gparted installed.
I have looked at the man page for the dd command although I don't know how it would work in my particular example. I have also looked at Clonezilla although I don't know if this is appropriate for what I want to do. I have read a few similar threads although I found some of them difficult to follow.

Any advice would be very greatly appreciated and if there's any further information required I'd be more than happy to provide it.

Thank you in advance.

---

### Post by Irony on 2011-01-04
Copying is extremely simple. Use gparted from a live CD to format your new drive as your want it (assign a label name to each partition to make it easy to identify). Mount the old and new partitions and then copy your ubuntu distro from the old drive to the new drive like this;

```
sudo cp -ax /media/file1/. /media/file2/.

```
Once copied edit /etc/fstab in file2 (the new drive) so that root has the correct blkid id (sudo blkid).

Now sort out grub;

```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo grub-install /dev/sda
```

Note that you will have to replace my example names and partitions with your own. Once booted into the new copy perform;
```

sudo update-grub
```

---

### Post by Irony on 2011-01-04
Double post

---

### Post by slgtheindividual on 2011-01-04
Thankyou, this looks like what I need to do but could you just explain the commands to me step by step please so that I know how to apply it to my needs, I'm quite new to ubuntu.

Sorry to be a pain, thank you in advance.

---

### Post by SaintDanBert on 2011-01-04
There is software called "Clonezilla".  Its purpose is to clone partitions or whole drives.

I routinely do this:
[list]
[*] put a fresh, larger drive into my laptop
[*] put the olde, small drive into an external usb box and connect it
[*] put a clonezilla CD into the CD/DVD and boot
[*] use clonezilla to clone from-USB to internal
[*] reboot
[/list]

Grub-whatever just works.
Multi-OS-boot just works.
Existing partitions just work.
New drive has whatever as freespace that I can use however I want.
Olde drive goes on the shelf as "backup" in case something goes foul.
(After a while I'll recycle the olde drive into an archival drive.)

Clonezilla has options to resize and move partitions during the clone operation. Takes some learning, but it is straight forward.

NOTE -- What others said about copy and gparted and friends is all true. Clonezilla has most of that built-in.

Bonne chance,
~~~ 0;-Dan

---

### Post by seawolf167 on 2011-01-04
> **SaintDanBert said:**
> There is software called "Clonezilla".  Its purpose is to clone partitions or whole drives.

I routinely do this:
[LIST]
[*] put a fresh, larger drive into my laptop
[*] put the olde, small drive into an external usb box and connect it
[*] put a clonezilla CD into the CD/DVD and boot
[*] use clonezilla to clone from-USB to internal
[*] reboot
[/LIST]

Grub-whatever just works.
Multi-OS-boot just works.
Existing partitions just work.
New drive has whatever as freespace that I can use however I want.
Olde drive goes on the shelf as "backup" in case something goes foul.
(After a while I'll recycle the olde drive into an archival drive.)

Clonezilla has options to resize and move partitions during the clone operation. Takes some learning, but it is straight forward.

NOTE -- What others said about copy and gparted and friends is all true. Clonezilla has most of that built-in.

Bonne chance,
~~~ 0;-Dan

+1 for [clonezilla]("http://clonezilla.org/")

You can optionally go from drive-to-drive or just image/restore individual partitions (along with a number of other options), plus it is very easy to use

---

### Post by Irony on 2011-01-04
> **slgtheindividual said:**
> Thankyou, this looks like what I need to do but could you just explain the commands to me step by step please so that I know how to apply it to my needs, I'm quite new to ubuntu.

The way I would do it is this.

With the old drive still in the laptop I would connect an external usb drive and copy my current ubuntu into a folder on the external usb drive (which is formatted in the same format as the current ubuntu) by booting up into ubuntu and performing the following command;

```
sudo cp -ax /. /media/usbdrive/folder/.
```

Where 'folder' is the name of a folder I first created in the external usb drive. The copy command means copy the contents of currently booted ubuntu into /media/usbdrive/folder. Yes this can be done from a currently booted ubuntu.

The cursor would blink then give an error about gvfs and then finally complete (depending on how much there is to copy). Ignore the gvfs error.

I would then put the new drive into the laptop and format it with gparted in an ubuntu live CD. I would do one one partition for the installation say sda1 (labelling it ubuntu) and one for swap sda2 (labelling it swap).

Then I would plug in the external usb drive and using disk utility (under administration) mount media/ubuntu and /media/usbdrive/folder/ and then perform the following command;

```
sudo cp -ax /media/usbdrive/folder/. /media/ubuntu/.
```

i.e. copy the contents of the folder containing the copied ubuntu to the folder called ubuntu (sda1).

After copying I would then go to the /media/ubuntu/etc/fstab and replace the blkid id of root and swap with the new block ids determined by doing;

```
sudo blkid
```

Then I would do;

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo grub-install /dev/sda
```

Which chroots me into sda1 as though I was booted into it and then installs grub to the MBR of sda and points it to the grub files in sda1. I would then actually boot into sda1 and perform the following to make sure it was updated correctly;

```
sudo update-grub
```

---

### Post by slgtheindividual on 2011-01-06
Thank you very much.

---

### Post by SaintDanBert on 2011-01-06
1.  Please post whatever you actually decided to do that resolved your issues.  That way others can know to do similar things.

2.  Please use Thread Tools to mark this item SOLVED.

Congratualations,
~~~ 0;-Dan

---

