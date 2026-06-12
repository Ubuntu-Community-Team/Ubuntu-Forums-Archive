---
title: "Gparted: Destroying data on an old hard drive"
date: 2011-12-23
forum: General Help
---

### Post by evenrelation on 2011-12-23
Hi

This is not an OS question, but if I erase all partitions from a hard drive and throw in the trash, what is the likelihood that some garbage genius out there will gain access to the data?

Will all contents of a hard drive be safely destroyed if I use gparted on the Ubuntu live cd?

---

### Post by coffeecat on 2011-12-23
> **evenrelation said:**
> 
This is not an OS question, but if I erase all partitions from a hard drive and throw in the trash, what is the likelihood that some garbage genius out there will gain access to the data?

A very high likelihood that they will be able to recover most of your data. All it needs is a data recovery application such as photorec, and you don't need to be a genius or a data recovery expert to be able to use it.

> **evenrelation said:**
> Will all contents of a hard drive be safely destroyed if I use gparted on the Ubuntu live cd?

No. You need to overwrite the whole hard drive. The terminal command shred is good for this.

---

### Post by saneearth on 2011-12-23
Honestly if you are going to throw the drive in the trash a good sledge hammering is the solution I often use. It is not a technical solution, but very practical and effective.

---

### Post by Basher101 on 2011-12-23
if you are going to throw it away anyways, just hit a wall with it...mechanical hard drives aren't very shock resistant. But if you want to go 100% sure, do whats posted above me and then hit a wall with it :D

---

### Post by oldfred on 2011-12-23
Best to recycle if you can after you have destroyed data.

Our local community used to have an annual electronics recycling event, but now does it monthly.

**As of** **January 1, 2012: TVs, computers (and  laptops), monitors, printers, computer peripherals, VCRs/DVD players,  gaming systems, MP3 players and other electronic items will be banned  from Illinois landfills.**

---

### Post by QIII on 2011-12-23
There is a utility called dban (or Derik's Boot and Nuke) that is great for wiping disks.  You can go full DoD level and medieval on the thing.

But be careful:  It is a dangerous thing and you can end up wiping out more disks than you want.

I recommend unplugging all drives but the one you want to wipe and running the CD with only the one you want to wipe plugged in.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by quadproc on 2011-12-23
Other posters have mentioned good ways to destroy data on a disk - here is another way:

Use dd to copy from /dev/zero to the target disk.  Copy enough bytes to be sure that you did the whole disk.

Be careful!  dd allows you to write *anything* to *any part* of a disk so be sure that you point it to the correct disk.

quadproc

---

### Post by Bobhuber on 2011-12-23
> **evenrelation said:**
> Hi

This is not an OS question, but if I erase all partitions from a hard drive and throw in the trash, what is the likelihood that some garbage genius out there will gain access to the data?

Will all contents of a hard drive be safely destroyed if I use gparted on the Ubuntu live cd?
No > Download and burn a CD ISO  with Parted Magic
It has all the utilities to do anything and everything to a disk drive (including SSD drives)

---

### Post by Synoc on 2011-12-23
the REAL question is, would you be better suited to keep the disk? I have a spare HHD in my PC that I don't mount on boot. I back up all my important files there, many others mount their entire OS to a small drive and their /home directory to the much larger one. that way if something gets corrupt they can simply unmount the /home, and reimage the OS drive. if I get a smaller drive I plan on doing just that.

---

### Post by audiomick on 2011-12-23
> **Synoc said:**
> the REAL question is, would you be better suited to keep the disk? I have a spare HHD in my PC that I don't mount on boot. I back up all my important files there, many others mount their entire OS to a small drive and their /home directory to the much larger one. that way if something gets corrupt they can simply unmount the /home, and reimage the OS drive. if I get a smaller drive I plan on doing just that.
This is a very good point. The only good reason I can think of for throwing out a drive would be that the machine is a laptop with only one drive slot and you have bought a bigger drive, or the drive is a complete write off.

In the first case, you could consider getting an external case for the drive and keep using it, in the second you would be able to wipe it because it doesn't run anymore, and for this reason shouldn't have to worry about wiping it.

---

### Post by collisionystm on 2011-12-23
you can use badblocks

it comes with ubuntu.

It rights everything on the drive to 0

It is used for checking for bad sectors so you know you are installing a reliable harddrive in a server.
However it will work for wiping it out. Its very thorough. Set it for a 3 passes. It will take a LONG TIME for a large drive. But Like I said writing everything to 0 is the best way to wipe that thing out.

---

### Post by spcwingo on 2011-12-24
You could always (from a live CD) just use this command:

```
sudo dd if=/dev/zero of=/dev/sda
```

That is, assuming that the drive designation is "sda".  You can find out by running this command in a terminal:

```
sudo fdisk -l
```

---

### Post by fdrake on 2011-12-24
> **quadproc said:**
> Other posters have mentioned good ways to destroy data on a disk - here is another way:

Use dd to copy from /dev/nul to the target disk.  Copy enough bytes to be sure that you did the whole disk.

Be careful!  dd allows you to write *anything* to *any part* of a disk so be sure that you point it to the correct disk.

quadproc
you cannot read from /dev/null (only write to it). even if dd does not output an error you did not overwrite your data. for that use /dev/zero (or /dev/random , but is very slow..)

---

### Post by dcstar on 2011-12-24
The encoding of modern drives (anything made in the last 15-20 years) basically writes random patterns to the physical drive whether **you** decide to write sectors full of zeros, ones or whatever. Any advice to use a particular value is based on delusion.

If you want to Securely Erase a drive then use a NIST boot disk that does this using the inbuilt ATA Secure Erase function, or use the hdparm method for achieving the same thing.

The amount of total BS that persists on this subject is amazing.

---

### Post by collisionystm on 2011-12-24
> **dcstar said:**
> The encoding of modern drives (anything made in the last 15-20 years) basically writes random patterns to the physical drive whether **you** decide to write sectors full of zeros, ones or whatever. Any advice to use a particular value is based on delusion.

If you want to Securely Erase a drive then use a NIST boot disk that does this using the inbuilt ATA Secure Erase function, or use the hdparm method for achieving the same thing.

The amount of total BS that persists on this subject is amazing.

In regards to this.

[http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf](http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf)

---

### Post by quadproc on 2011-12-24
> **fdrake said:**
> you cannot read from /dev/null (only write to it). even if dd does not output an error you did not overwrite your data. for that use /dev/zero (or /dev/random , but is very slow..)
Yes, my mistake.  I meant to say /dev/zero so I have corrected my original post.

quadproc

---

### Post by dcstar on 2011-12-27
> **collisionystm said:**
> In regards to this.

[http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf](http://csrc.nist.gov/publications/nistpubs/800-88/NISTSP800-88_rev1.pdf)

If you want a GUI tool to boot and use the ATA Secure Erase feature, this might be worth using:

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

With instructions here:

[http://www.ocztechnologyforum.com/forum/showthread.php?81321-Secure-Erase-With-bootable-CD-USB-Linux..-Point-and-Click-Method](http://www.ocztechnologyforum.com/forum/showthread.php?81321-Secure-Erase-With-bootable-CD-USB-Linux..-Point-and-Click-Method)

Here is a HOWTO on using the hdparm method:

[https://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/](https://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/)

---

