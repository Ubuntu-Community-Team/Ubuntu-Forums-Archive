---
title: "Cant save files, cant re-install linux, can't format hard drive, want to die"
date: 2012-07-30
forum: General Help
---

### Post by Michaelbyrne on 2012-07-30
Hi everyone,

I've got 32 bit Ubuntu 12.04 on a Samsung N130 Netbook (no CD Drive). Ubuntu is the only OS I have, there is no Windows or other partitions for other OS's.

About a week ago my system stopped saving files - all newly created files, downloads or changes to the machine reverse back to how it was a week ago upon rebooting the system. 

I thought my OS might be in some sort of 'read-only' mode, so I've ran 'sudo mount -o remount /'. This hasn't altered anything.

After fiddling with this for a long time I decided to bite the bullet and re-install my OS. When I try I get an error stating 'the ext4 file system creation in partition #1 (0,0,0)(sda) failed'. After scouring the forums I found several solutions. I tried different distributions of ubuntu, I've tried using different USB devices to boot from, I must have burned at least 15 copies of different Ubuntu distributions to try.

Then I tried to partition my hard drive from within a Live boot from the USB using GParted so that I could install a fresh ubuntu to this partition. That came back with an error.

Then I've tried to format the whole Hard drive and wipe it completely using 'sudo mkfs /dev/sda'. This worked - the hard drive appeared free of data entirely in Gparted and the installer said that 'no operating system is present'. However when I tried to install ubuntu again I was faced with the same 'ext4 file' problem.

Upon a reboot from the internal hard disk, I can see that my drive was not formatted at all, and I'm back to the same state.

My head hurts from how much I'm banging it against a brick wall.

Michael ](*,)

---

### Post by jmcgovern on 2012-07-30
Unfortunately it would appear that the hard drive is essentially dead if you're running into that many errors writing to disk.

---

### Post by Mopar1973Man on 2012-07-30
Possible hard drive failure? :confused:

---

### Post by TheFu on 2012-07-30
Sounds like failing hardware - disk controller or HDD or cable or perhaps a cracked motherboard.  Failing power supplies also cause odd behaviors.

First thing, I'd boot off a rescue distro and run **fsck /dev/sda1**

I don't think that **mkfs /dev/sda** is the right command. You need to 
* partition
* mkfs
* then mount.

If a fresh install isn't doing this, I'm back to the failing hardware.

I don't think most people trying to install on the full device. You really need a partition first /dev/sda1 for example.

The sudo mount -o remount is an interesting idea. I think **sudo touch /forcefsck** would have been more helpful if you could ever get the file system mounted read-write.  Under a rescue boot, getting that empty file at the base of the partition directory will force an fsck check during the next reboot. That is usually easier than going into single user mode or finding an outside boot CD - at least for me.

---

### Post by efflandt on 2012-07-31
With gparted, try creating an msdos partition table, then try creating an ext4 partition.  If that either chokes, or gparted does not recognize the filesystem on the partition it just formatted, your drive is probably failing.

I was playing around with an old 60 GB drive that was failing.  I was able to successfully format something like 32 GB plus swap.  But about the latter 25 GB would either fail to format, gparted did not recognize it just after it formatted it (? for filesystem type), or one time it appeared to successfully format, but I think I got errors trying to actually use it.  And I believe SMART kept complaining about immanent drive failure during boot.

---

### Post by TheFu on 2012-07-31
> **efflandt said:**
> SMART kept complaining about immanent drive failure during boot.

If SMART sees the failure coming, it is already tooooooooo late.

I didn't make this suggestion earlier, but if the errors are only lazy bits, there are some HDD programs that exercise the entire drive heavily. Sometimes lazy bits in certain locations can be reset and the drive is fine for another 2-4 yrs.  

The only one I know that actually does something AND is under $2000 is **Spinrite **for $80-$90.  It can't fix failing hardware, but it will certainly let you know if your hardware is fine and will correct most bit-rot issues (most commonly seen on Windows boot BSOD).  I've had drives act like they were failing, then swapped in a replacement and restored from a backup.  Taking the *failing* drive to another PC and running spinrite for a few days corrected all the errors and gave me confidence to put in those drives back into service. I'm running 2 servers at home on drives like that today. I don't even worry about them. Though I still perform automatic nightly backups to different storage.  Backups (automatic and daily) are just good practice.

---

