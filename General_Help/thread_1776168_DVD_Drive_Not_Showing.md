---
title: "DVD Drive Not Showing"
date: 2011-06-05
forum: General Help
---

### Post by terrykiwi83 on 2011-06-05
Have finally migrated fully to Linux now after many years dual booting. But have one teething issue at the moment.

Am running Ubuntu 10.10 Maverick (Linux Mint 10) x64bit

Well I have two internal DVD Drives, one uses a SATA connection the other a basic IDE connection.

The IDE drive currently works and shows up, but the SATA drive doesn't show up anywhere.

The SATA drive is a TSST-Corp DVDRW Drive
The IDE Drive is a HP DVDRW Drive (640 model or something)

So the funny thing is, their is power to the TSST drive and it opens etc but just doesn't get recognized by the OS.

But if I restart the computer and pop the Live CD into its drive it will boot into the Live CD and show up just fine.

So am just looking for any ideas on how to get the SATA drive to work on my setup.

Thanks in advance.

---

### Post by terrykiwi83 on 2011-06-05
bump, anyone :(

---

### Post by terrykiwi83 on 2011-06-06
So hasn't anyone had this problem before :(

---

### Post by jwcalla on 2011-06-06
Are you saying that when you put a disc in, it doesn't mount in /media and doesn't show up in nautilus?  I seem to have that problem with (movie) DVDs that are encrypted sometimes, but data DVDs are ok.

Or are you saying that the drive is not even listed in the Disk Utility program?

---

### Post by terrykiwi83 on 2011-06-06
thanks for the reply, the drive isn't even listed in the disk utility program.

:(

---

### Post by terrykiwi83 on 2011-06-06
Ok I have done a bit of research and after looking in my /etc/fstab file there is no mention of any of my dvd drives.

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
# /home/THEVAULT was on /dev/sdb7 during installation
UUID=0c6ea1fe-9ce0-4005-b3cf-037ba9d10410 /home/THEVAULT  ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=7786982c-3ea4-4488-8284-7e19eb7adfd1 none            swap    sw              0       0
/dev/sdb6       none            swap    sw              0       0
/dev/sda1	/media/TERA	ntfs	defaults	0	0

```

This is pretty unusual IMO as am sure its supposed to even mount the one drive that I can use? even though at the moment I cannot burn disks with the HP Drive something about permissions keeps coming up in k3b.

I also had a look at lshw -c disk to see whether my SATA TSST Corp DVD Drive would be shown and nope it isn't there, what would cause it not to show? It only shows my HP Drive?

```

terry@ORACLE ~ $ sudo lshw -c disk
[sudo] password for terry: 
  *-cdrom                 
       description: DVD writer
       product: DVD Writer 640b
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: E152
       serial: [HP      DVD Writer 640b E15204/11/17KRKA1544
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD10EARS-00Y
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 80.0
       serial: WD-WCAV5F214920
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ccb5665f
  *-disk:1
       description: ATA Disk
       product: WDC WD7500AACS-0
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCASP0031418
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f01ff0bb
  *-disk
       description: ATA Disk
       product: KINGSTON SNV425S
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: D100
       serial: 07ta60007353
       size: 59GiB (64GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4354d258

```

---

### Post by jwcalla on 2011-06-06
I don't think DVD drives are listed in fstab anymore since they tend to be automounted.  My fstab doesn't list my DVD drive either.

I'm not sure what your problem is, since it seems like the OS doesn't even recognize that there's hardware there.  Maybe the SATA controller isn't exposing it for some reason, or there's a problem with the chipset driver.

Have you tried disconnecting the HP drive and then seeing if the SATA drive can be detected?

---

### Post by mc4man on 2011-06-06
The above and what may be interesting is to boot to a liveCD using the ide drive and see if the sata drive is detected (adjust in bios if needed

did you put this box together yourself or buy as is or close to?

---

### Post by terrykiwi83 on 2011-06-06
> **jwcalla said:**
> I don't think DVD drives are listed in fstab anymore since they tend to be automounted.  My fstab doesn't list my DVD drive either.

I'm not sure what your problem is, since it seems like the OS doesn't even recognize that there's hardware there.  Maybe the SATA controller isn't exposing it for some reason, or there's a problem with the chipset driver.

Have you tried disconnecting the HP drive and then seeing if the SATA drive can be detected?

thanks for the advice, I have tried disconnecting the IDE drive and when I reboot back into Ubuntu there is nothing - no drives.

Just for the record both drives work together in Windows 7, so it must be some misconfiguration with Ubuntu somewhere along the line.

Is there no way (or a program) to auto-detect devices on the SATA bus?

---

### Post by jwcalla on 2011-06-06
> **terrykiwi83 said:**
> Is there no way (or a program) to auto-detect devices on the SATA bus?

I think that's what the lshw command does.  But if they're not listed (probably as sr1) in /dev/disk/by-path or /dev/block, then it seems the kernel isn't finding the hardware at all.

You could try switching the SATA connection to a different one on the motherboard to see if it that works.  And if not, I'd say it's something drive specific, and you might have to look for a driver or any known bugs with running that particular drive model in linux.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **terrykiwi83 said:**
> So hasn't anyone had this problem before :(

Did you check your BIOS?  Do you have the DVD and CD drives on the first and second buses?  It sounds like to me you have had a hardware upgrade and that they didn't get the bus configuration in order.

---

### Post by jwcalla on 2011-06-06
Just doing a quick Google search on TSST problems, I've seen everything from 1) disabling it in the BIOS, 2) doing "modprobe piix" to load a driver, 3) disabling apic in the grub config, 4) could be AHCI / APM related.

Seems like it's disk controller related.  What's the motherboard?  Is the drive set up as a master / slave relationship in the BIOS?

You can use "sudo lspci -vvvnn" and look for the IDE interface sections and verify that each SATA controller is detected and see which kernel module is loaded.  (E.g., my MB has two SATA controllers with two ports on each controller.)

---

### Post by terrykiwi83 on 2011-06-06
hey guys thanks for all the suggestions, I have actually now fixed it.

What I believe the problem was is the SATA DVD RW Drive was plugged into one of my SATA 3.0 Ports and not the SATA 2.0 Port - when I changed it to the standard SATA Port it worked a charm.

Seems Ubuntu doesn't like SATA3 at the moment?

Thanks for all the ideas :)

---

### Post by jwcalla on 2011-06-06
> **terrykiwi83 said:**
> hey guys thanks for all the suggestions, I have actually now fixed it.

What I believe the problem was is the SATA DVD RW Drive was plugged into one of my SATA 3.0 Ports and not the SATA 2.0 Port - when I changed it to the standard SATA Port it worked a charm.

Seems Ubuntu doesn't like SATA3 at the moment?

Thanks for all the ideas :)

A newer kernel version might have SATA3 support for your chipset.  I guess the kernel that shipped w/ 10.10 is getting a bit old now.

See this for some info:  [http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/](http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/)

---

### Post by linuxinstalledfromhdd on 2011-06-06
You can always update to the latest kernel too.  Just go into synaptic, and select the one you want and the headers to go with it.

---

### Post by jwcalla on 2011-06-06
> **linuxinstalledfromhdd said:**
> You can always update to the latest kernel too.  Just go into synaptic, and select the one you want and the headers to go with it.

Can you do that?  I'd like to upgrade to 2.6.39 myself without downloading it and compiling, but I don't see it in synaptic.  Unless I find a non-canonical PPA and add it to my software sources.

---

