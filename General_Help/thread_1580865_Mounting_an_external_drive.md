---
title: "Mounting an external drive"
date: 2010-09-24
forum: General Help
---

### Post by oygle on 2010-09-24
Running 10.04, and I have an external HDD, which has USB/SATA switch. It is all hooked up okay, data and power cables ready, I boot up Ubuntu, then power up the external drive, but Ubuntu doesn't mount it.

The only way I can get it to mount, is to go into BIOS, then power up the external drive, exit BIOS, then the drive is recognised, and then after logging into Ubuntu, there is an icon there, to mount the drive.

I looked through the manual for the external drive, and apparently, you shouldn't have it powered up before the computer is powered up, it has to be after.

In BIOS, plug and play is disabled, I don't know if that makes a difference.

How can this be setup, so that after booting, I can turn the power on, and the drive will be recognised. It is for backup only, so no point in having it running unecessarily.

When it is mounted, the info from the mount command shows as

> /dev/sdb1 on /media/4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6 type ext3 (rw,nosuid,nodev,uhelper=udisks)

Is it just a matter of setting this up under /etc/fstab and/or /etc/mtab ??

It would be nice to have it mounted properly and give it a label, as nautilus has it as "/media/4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6"

On another note, but related, the fdisk -l command shows the following for one HDD

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033ea0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17447   140136719   83  Linux
/dev/sda2           17447       24321    55220961+   f  W95 Ext'd (LBA)
/dev/sda5           23565       24321     6080571   82  Linux swap / Solaris
/dev/sda6           17447       23564    49139712   83  Linux


but only /dev/sda1 and /dev/sda6 are mounted. I would like to 'see' what is in /dev/sda2 , as soon the HDD will be reformatted.

Oygle

---

### Post by wombil on 2010-09-24
Hello oygle,
 I'm not much on terminal commands but the way I power on and off my external drive is to have it on a powerboard with individual switches.Mostly I switch it on before I power up if i need it.
  AND HERE"S THE BEST PART,My name is oigle,all the family and friends call me oigle.Not many of us around,we got to stick together.
 best of luck with it brother.

---

### Post by oygle on 2010-09-24
Hi oigle, thanks for your help. Yes, not many of us around, alright.  :)

The drive case does have a power switch, but I thought it was better to not have it spinning when the computer powers up.  Anyway, possibly a mount command in one of the /etc files will do it.

---

### Post by coffeecat on 2010-09-24
> **oygle said:**
> Running 10.04, and I have an external HDD, which has USB/SATA switch. It is all hooked up okay, data and power cables ready, I boot up Ubuntu, then power up the external drive, but Ubuntu doesn't mount it.

The only way I can get it to mount, is to go into BIOS, then power up the external drive, exit BIOS, then the drive is recognised, and then after logging into Ubuntu, there is an icon there, to mount the drive.

In theory, Ubuntu *should* automount all USB drives as soon as they are powered on. But this sounds to be a firmware problem in the USB drive. What make and model is it? It's not a Seagate by any chance? :(

> **oygle said:**
> In BIOS, plug and play is disabled, I don't know if that makes a difference.

Or, yes, it could be a conflict between the BIOS and the drive's firmware. Try enabling plug and play. That might be the solution.

Before you do that, plug the drive in, switch it on, wait a few moments and then open a terminal and try:

```
dmesg | tail
```Post the output. that will tell us if the device is actually being detected because I think this is a detection failure, not a mounting failure.

> **oygle said:**
> It would be nice to have it mounted properly and give it a label, as nautilus has it as "/media/4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6"

Agreed - that string of characters is the UUID of the mounted partition, which is useful but unwieldy. Assuming the partition you want to label is sdb1 (please check this), you can create a partition label with:

```
sudo e2label /dev/sdb1 label
```The device must be recognised for this to work. It doesn't matter whether it's mounted or not. Then, the next time it will be mounted on /media/label.

> **oygle said:**
> but only /dev/sda1 and /dev/sda6 are mounted. I would like to 'see' what is in /dev/sda2 , as soon the HDD will be reformatted.

Have a look in the Places menu. It will be there. Simply click on it and it will automount. Unless it has a partition label, it will be identified by size in GiB.

---

### Post by oygle on 2010-09-24
> **coffeecat said:**
> In theory, Ubuntu *should* automount all USB drives as soon as they are powered on. But this sounds to be a firmware problem in the USB drive. What make and model is it? It's not a Seagate by any chance? :(

Yes, it is a Seagate ST3500320AS, 500Gb. It's in an external case, and can be run by USB or SATA. I have it setup for SATA (eSATA). It didn't automount.

> **coffeecat said:**
> Or, yes, it could be a conflict between the BIOS and the drive's firmware. Try enabling plug and play. That might be the solution.

I will try that and see what happens. In regards to USB devices, I just plug them in, and they are always automounted.  But this is eSATA.

> **coffeecat said:**
> 
Before you do that, plug the drive in, switch it on, wait a few moments and then open a terminal and try:

```
dmesg | tail
```Post the output. that will tell us if the device is actually being detected because I think this is a detection failure, not a mounting failure.

That was exactly what I tried initially, as I had read some posts here. When I switched it on, no automount, and the 'dmesg' produced no info on it.

> **coffeecat said:**
> Agreed - that string of characters is the UUID of the mounted partition, which is useful but unwieldy. Assuming the partition you want to label is sdb1 (please check this), you can create a partition label with:

```
sudo e2label /dev/sdb1 label
```The device must be recognised for this to work. It doesn't matter whether it's mounted or not. Then, the next time it will be mounted on /media/label.

Yes, it is /dev/sdb1 that I want to mount, it is the external drive. I tried that command, it seemed to work okay, although /dev/sdb1 was already mounted at the time.

> **coffeecat said:**
> Have a look in the Places menu. It will be there. Simply click on it and it will automount. Unless it has a partition label, it will be identified by size in GiB.

The external drive was definitely in the Places menu, but only if I went into BIOS on Boot.

In regards to the other partition (win95 one), I did try this ..

```
$ **sudo mkdir /media/sda2**

$ **sudo mount -t vfat /dev/sda2 /media/sda2**
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ **dmesg | tail**
[19463.816122] do_floppy=f806e660
[19463.816124] fd_timer.function=f8074810
[19463.816127] cont=f80772ec
[19463.816129] current_req=cb9bb640
[19463.816131] command_status=-1
[19463.816133] 
[19463.816138] floppy0: floppy timeout called
[19463.816143] end_request: I/O error, dev fd0, sector 0
[21034.671901] FAT: invalid media value (0x74)
[21034.671909] VFS: Can't find a valid FAT filesystem on dev sda2.
```

Oygle

---

### Post by coffeecat on 2010-09-24
> **oygle said:**
> Yes, it is a Seagate ST3500320AS, 500Gb. It's in an external case, and can be run by USB or SATA. I have it setup for SATA (eSATA). It didn't automount.

I will try that and see what happens. In regards to USB devices, I just plug them in, and they are always automounted.  But this is eSATA.

I've seen quite a few threads about Seagate USB drives not mounting, but you're using eSATA. Sorry I missed that before. Does any firmware get in the way when you use eSATA? I thought it was a more-or-less direct connection, but if firmware does come into the equation then this may be the dreaded Seagate striking again. Ever since I bought a MacMini which came with one of a batch of Seagate drives that failed catastrophically while still fairly new I've avoided Seagate like the plague. I replaced that drive with a Hitachi after opening the MacMini up. That was fun! :-s

Have you got another enclosure (not Seagate) handy? Could you take out the bare drive and put it in the other enclosure too see whether it behaves itself? That would, at least, confirm or exclude the enclosure firmware as being the problem. 

> **oygle said:**
> That was exactly what I tried initially, as I had read some posts here. When I switched it on, no automount, and the 'dmesg' produced no info on it.

No info about that drive with dmesg confirms what I suspected. The device is not being detected, hence nothing to mount.

> **oygle said:**
> Yes, it is /dev/sdb1 that I want to mount, it is the external drive. I tried that command, it seemed to work okay, although /dev/sdb1 was already mounted at the time.

It'll appear next time you mount. Also the icon on the desktop will have the same label, which is useful.

But this bit sounds serious:

> **oygle said:**
>  The external drive was definitely in the Places menu, but only if I went into BIOS on Boot.

In regards to the other partition (win95 one), I did try this ..

```
$ **sudo mkdir /media/sda2**

$ **sudo mount -t vfat /dev/sda2 /media/sda2**
mount:[COLOR=red] wrong fs type, bad option, bad superblock on /dev/sda2,[/COLOR]
```[COLOR=red]       missing codepage or helper program, or other error[/COLOR]
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ **dmesg | tail**
[19463.816122] do_floppy=f806e660
[19463.816124] fd_timer.function=f8074810
[19463.816127] cont=f80772ec
[19463.816129] current_req=cb9bb640
[19463.816131] command_status=-1
[19463.816133] 
[19463.816138] floppy0: floppy timeout called
[19463.816143] end_request: I/O error, dev fd0, sector 0
[21034.671901] FAT: invalid media value (0x74)
[21034.671909] VFS: [COLOR=red]Can't find a valid FAT filesystem on dev[/COLOR] sda2.[/code]Oygle

Sounds like a corrupted filesystem. Since it's FAT32 you could try chkdsk from Windows. Presumably, since that's an old W95 install, you'd have to take the drive out, put it in an enclosure and run chkdsk from another Windows machine. Or - a last resort - use photorec from testdisk in Ubuntu to recover files. That's not a fun thing to do I can assure you.

---

### Post by oygle on 2010-09-24
> **coffeecat said:**
> Does any firmware get in the way when you use eSATA? I thought it was a more-or-less direct connection, but if firmware does come into the equation then this may be the dreaded Seagate striking again.

Basically, the SATA cable from the external drive case just goes straight into the SATA channel on the motherboard. I'd say firmware or drivers wouldn't be necessary. There is some info [here](http://www.coolice.com.au/catalog/product_info.php?products_id=8714) and it says it is 'hot swap plug and play, so I should try the BIOS setting to 'yes' for Plug and Play, and see if it makes a difference.

Sorry, I don't have any hard drive to try in the enclosure.

That's good that it will appear next time I mount it. After doing that command, under Nautilus, it did have a 'label' there.

If the Win95 partition is corrupted, I don't think I will worry about it, as there would have to be old data there, if any at all. If I look at this ..

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 17447 140136719 83 Linux
/dev/sda2 17447 24321 55220961+ f W95 Ext'd (LBA)
/dev/sda5 23565 24321 6080571 82 Linux swap / Solaris
/dev/sda6 17447 23564 49139712 83 Linux 

it would seem the W95 partition is 'part' of a logical partition that spans /dev/sda6 and /dev/sda5. Maybe GParted might tell me some more info there, but I don't think I will worry about it; seems no 'easy' way to mount that partition and view what's there.

Thanks for your help,

Oygle

---

### Post by coffeecat on 2010-09-24
> **oygle said:**
> If the Win95 partition is corrupted, I don't think I will worry about it, as there would have to be old data there, if any at all. If I look at this ..

```

...
/dev/sda2 17447 24321 55220961+ f W95 Ext'd (LBA)
...

```it would seem the W95 partition is 'part' of a logical partition that spans /dev/sda6 and /dev/sda5.

Whoops! Mucho embarrassment here. :oops: The "f W95 Ext'd (LBA)" means that sda2 is an extended partition which "contains" your logicals, sda5 and sda6. If there was a FAT partition there once, the data will have been (mostly) overwritten. Sorry I missed that. The "f W95 Ext'd (LBA)" is how extendeds used to appear in fdisk. What I don't understand is that you are running 10.04, and in my 10.04, fdisk shows me this for my sda2 extended partition:

```
/dev/sda2           26109       60802   278670336    5  Extended
```Which is, at least, a bit more obvious. Your profile says Jaunty. Did you get that fdisk output from Lucid or Jaunty?

Anyway - best of luck with the rest. Thanks for confirming that eSATA goes straight to the drive. I thought that was the case. Perhaps the BIOS setting is the answer.

---

### Post by spreda on 2010-09-24
[QUOTE=oygle;9883515]

Device Boot Start End Blocks Id System
/dev/sda1 * 1 17447 140136719 83 Linux
/dev/sda2 17447 24321 55220961+ f W95 Ext'd (LBA)
/dev/sda5 23565 24321 6080571 82 Linux swap / Solaris
/dev/sda6 17447 23564 49139712 83 Linux 			 		


forgive me if someone else has pointed this out,but from the data above
/dev/sda1 is a bootable primary partition (max allowed = 4)
/dev/sda2      is an extended partition which counts as a primary and _contains_ /dev/ sda5 & /dev/sda6 , both logical partitions: I don't know max logical, I have had >20 without problems. 
this may save you a bit of messing about trying to find a w95 partition which is only a folder for the logical partitions. 
cheers, bill

---

### Post by oygle on 2010-09-24
I got the fdisk output from Lucid. Am using the external drive to backup all the data and config. files, etc, and will then format the (internal) drive, and do a fresh install of Lucid.

Yes, the BIOS setting should do the trick, however any USB is recognised as soon as it is plugged into Ubuntu box, but maybe USB works different, in that the power side of things forces an automount.

Would still like to setup a mount in those /etc paths, and even if the external is powered off, I would think it would just ignore the setting.

Thanks,

Oygle

PS  Thanks Bill, for the clarification on those partitions.

---

### Post by coffeecat on 2010-09-24
> **oygle said:**
> Would still like to setup a mount in those /etc paths, and even if the external is powered off, I would think it would just ignore the setting.

Here you go:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Although, once you've sorted out this automounting issue, you may find that having it automounted will do.

I notice that the drive is formatted ext3. You haven't mentioned permissions problems, so you may know about what I am about to say already. When an ext3 drive is automounted, it is mounted by root and you can't write to it. Not without some fiddling, such as chowning the mountpoint. What is not commonly understood is that this does not just change the ownership of the mountpoint, more importantly it changes the ownership of the whole filesystem. The new ownership is stored in the root of the filesystem - not just in the mountpoint. This is a subtle point but very useful.

Say the partition is mounted on /media/label. All you do is:

```
sudo chown yourusername: /media/label
```You can then copy to it without invoking root powers. More importantly, the next time it's mounted you can do the same. Very useful. Indeed, if you want to add an /etc/fstab line, a simple "defaults" in the options field will do. You don't have to muck around with UID and GID values.

---

### Post by oygle on 2010-09-24
Thanks for the link to Fstab; I will have to read up on it. The permissions side of things may be a problem for now, as I have been backing up data to the external drive, and have had to use 'sudo' to do it.

I did check the owner and group of a few files and paths here and there, they looked okay. However, I hope the permissions side of things, doesn't interfere with the restoring of all the data, from the external drive to the (newley installed) Lucid, after that (internal) drive has been reformatted.

There may be some 'gotchas' for me.  :oops:

---

### Post by coffeecat on 2010-09-24
> **oygle said:**
> The permissions side of things may be a problem for now, as I have been backing up data to the external drive, and have had to use 'sudo' to do it.

I did check the owner and group of a few files and paths here and there, they looked okay.

Depending what options you used with 'sudo cp' (if you used cp) you may have given some files root ownership, although it looks as though you haven't for the ones you've looked at. If any are owned by root, a quick...

```
sudo chown -R yourusername: /media/label
```... will do a recursive chown throughout the whole partition. Not quite sure what it would do to the lost+found folder or whether that matters.

Once you've chown'd the filesystem, the advantage is that you can do drag and drop copies, renames, everything from the GUI - no more sudo.

> **oygle said:**
>  However, I hope the permissions side of things, doesn't interfere with the restoring of all the data, from the external drive to the (newley installed) Lucid, after that (internal) drive has been reformatted.

There may be some 'gotchas' for me.  :oops:

Nothing that a bit of judicious chown-ing can't fix. Good luck! :)

---

### Post by oygle on 2010-09-24
Thanks for the tips on the recursive chown, very nice and handy.  :)

I may also do a recursive 'ls -al' and push the output to a file, on the external. Then after the restore, do the same on the internal drive, and then use Beyond Compare to see if any differences in the ('ls' output) files.

Will probably use BC to do the restore, if I use 'sudo bcompare' and then use it to copy, it does seems to keep all permissions, users, groups intact. Then I do a binary compare, just to make sure the copy side of things has gone okay.

After using Windooze for ages, I found that explorer in windooze often missed files, or only copied parts, so I kind of go a bit overboard now, to make sure a file is copied with the data consistent (==equal).

Thanks,

Oygle

---

### Post by oygle on 2010-09-24
I modified /etc/fstab as follows ..

> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6f8c7017-1480-45fe-b7f2-5024ae8e0ab1 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=7c71b76f-fc1e-4502-b1a3-b25a97a3d83d /boot           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a8bff4f4-006a-487e-8975-be211b372580 none            swap    sw              0       0
# / external hard drive - 500Gb
UUID=4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6 /media/externaldisk               ext3    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


powered the external drive on, system did not recognise it (expected), and then tried ..

> $ sudo mount -a
mount: special device UUID=4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6 does not exist

There must be a way to force the mount, other than at BIOS. Will read up a bit more on fstab.

---

### Post by oygle on 2010-09-25
Is there any method for this to be auto mounted, as Ubuntu recognises the external drive being powered up ?

Even when I power it up under BIOS, boot into Ubuntu (10.04), and I can see an icon called 'label', I cannot mount it, other than 'sudo'. When I click on the icon for 'label' , and select the 'mount' option, it refuses to mount.

Have to do this at terminal to mount it 

```
sudo mount /media/externaldisk
```

and ```
sudo umount /media/externaldisk
``` to unmount.

It can't be done via the GUI at all, unless I do a 'sudo nautilus' of course. I can now browse the external and modify files to it now, without being 'sudo', after the recursive 'chown'.

The external drive is defined in /etc/fstab ; surely there must be a way for it to be recognised by Ubuntu on powering up, and then mounted via the GUI.

Seems this is a [bug]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1478770")

Oygle

---

### Post by oygle on 2010-09-25
Now when I boot up, without the external powered off a msg

> The disk drive for /media/externaldisk is not ready yet or not present.

Continue to wait; or Press S to skip mounting or M for manual recovery.

Pressing M it comes up with a maintenance shell, which gives you an opportunity to mount it, Ctrl-D out of that, and it goes back to the message above.

Took an 'S' and it boots up okay, but of course, no icon for the external drive, as it is powered off. If I power it up, and try to mount it ..

> $ **sudo mount /media/externaldisk**
mount: special device UUID=4c7ae1b0-92ef-43eb-b79e-152cb0ec0eb6 does not exist

---

### Post by oygle on 2010-09-26
Well, using this external drive on **another** computer made a big difference. I booted up a 64 bit Ubuntu 10.04, which has no definitions for the external drive, in /etc/fstab

After booting, powered on the external drive, and with in 30 seconds, I see no icon up the top, but do see a 'label' in the Places.

Looked in the syslogs ..

> Sep 26 13:29:18  kernel: [ 6274.418687] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
Sep 26 13:29:18  kernel: [ 6274.418693] ata8: irq_stat 0x00000040, connection status changed
Sep 26 13:29:18  kernel: [ 6274.418697] ata8: SError: { PHYRdyChg CommWake DevExch }
Sep 26 13:29:18  kernel: [ 6274.418704] ata8: hard resetting link
Sep 26 13:29:28  kernel: [ 6284.470013] ata8: softreset failed (device not ready)
Sep 26 13:29:28  kernel: [ 6284.470020] ata8: hard resetting link
Sep 26 13:29:38  kernel: [ 6294.530011] ata8: softreset failed (device not ready)
Sep 26 13:29:38  kernel: [ 6294.530017] ata8: hard resetting link
Sep 26 13:29:39  kernel: [ 6295.460018] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 26 13:29:39  kernel: [ 6295.461018] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x100)
Sep 26 13:29:44  kernel: [ 6300.460024] ata8: hard resetting link
Sep 26 13:29:44  kernel: [ 6300.992516] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 26 13:29:44  kernel: [ 6300.993464] ata8.00: failed to IDENTIFY (I/O error, err_mask=0x100)
Sep 26 13:29:44  kernel: [ 6300.993468] ata8: limiting SATA link speed to 1.5 Gbps
Sep 26 13:29:49  kernel: [ 6305.990016] ata8: hard resetting link
Sep 26 13:29:50  kernel: [ 6306.520019] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 26 13:29:50  kernel: [ 6306.521354] ata8.00: ATA-8: ST3500320AS, SD15, max UDMA/133
Sep 26 13:29:50  kernel: [ 6306.521358] ata8.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Sep 26 13:29:50  kernel: [ 6306.523115] ata8.00: configured for UDMA/133
Sep 26 13:29:50  kernel: [ 6306.523122] ata8: EH complete
Sep 26 13:29:50  kernel: [ 6306.523217] scsi 7:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
Sep 26 13:29:50  kernel: [ 6306.523421] sd 7:0:0:0: Attached scsi generic sg3 type 0
Sep 26 13:29:50  kernel: [ 6306.524013] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Sep 26 13:29:50  kernel: [ 6306.524074] sd 7:0:0:0: [sdb] Write Protect is off
Sep 26 13:29:50  kernel: [ 6306.524078] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep 26 13:29:50  kernel: [ 6306.524108] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 26 13:29:50  kernel: [ 6306.524301]  sdb: sdb1
Sep 26 13:29:50  kernel: [ 6306.547909] sd 7:0:0:0: [sdb] Attached SCSI disk


The following commands showed that this computer (quite 'new') had no problems with recognising the external drive ..

> 
$ **mount**
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)
/dev/sdb1 on /media/label type ext3 (rw,nosuid,nodev,uhelper=udisks)
$ 
$
$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=be6ed9ab-c0c0-46cb-81d2-0231cbbc5ec8 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a7ab09fa-431c-4de5-81b6-0db6d8bddf21 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8f037509-b241-4338-8ae5-f5ab8b092561 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
$ 
$ 
$ **cat /etc/mtab**
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda3 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/username/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=username 0 0
/dev/sdb1 /media/label ext3 rw,nosuid,nodev,uhelper=udisks 0 0
$ 


This computer has an external eSATA jack, which should be the same as the card slot eSATA installed on the other computer. 

Both computers are running 10.04, one 32 bit, one 64 bit, so I would only assume that it is a mobo/BIOS combination, in that the newer mobo is able to recognise the drive just fine, no need for any definitions in /etc/fstab

Similarly, when I powered off the external, the 64 bit Ubuntu cleared the definition from /etc/mtab , and all went okay (I dismounted before powering off).

So, I can put up with the problems on the other computer, as the external will mostly be used on the 64 bit Ubuntu 10.04

Thanks,

Oygle

---

