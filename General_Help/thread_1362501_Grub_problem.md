---
title: "Grub problem"
date: 2009-12-23
forum: General Help
---

### Post by timbim on 2009-12-23
I've got a 9.10 install done fine, system runs fine once booted.  The problem is that now the system won't boot.  On power on, I get to a black screen, somthing about grub flashes up, and then I just get a cursor flashing at the top a black screen.  This continues indefinitely.  Can anyone shed any light on what might be going on here?

Thanks,
Tim.

---

### Post by lmarmisa on 2009-12-23
Try to reinstall Grub2 (read Reinstalling GRUB 2 section):

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Best regards,

Luis

---

### Post by timbim on 2009-12-23
Reading the Howto, I'm slightly confused.  I've got a separate /boot partition, so is this the only one I need to mount and do anything to?

---

### Post by lmarmisa on 2009-12-23
Read the chapter **METHOD 3 - CHROOT**

---

### Post by timbim on 2009-12-23
Should it not be possible to use the first method?  What I'm concerned about is that / is on a RAID5 array, while /boot is on sda1.  Is the /boot partition the only one I need to mount?

---

### Post by Leppie on 2009-12-23
could you download and run [meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the RESULTS.TXT it creates?

---

### Post by lmarmisa on 2009-12-23
Try this modified script:

```

sudo mount /dev/sdXY /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

```

If you wish to make a previous backup of the sda MBR (code area), type:

```

sudo dd bs=440 count=1 if=/dev/sda of=sda.MBRcodearea.backup.dd

```

Move the backup file to a persistent directory!!!

Best regards,

Luis

---

### Post by Leppie on 2009-12-23
> **lmarmisa said:**
> ```

sudo dd bs=440 count=1 if=/dev/sda of=sda.MBRcodearea.backup.dd

```

this should actually be:
```
$dd if=/dev/sda of=/home/mbr.old **_bs=446_** count=1
```

---

### Post by timbim on 2009-12-23
**@Leppie**

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00063d60

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       979,964       979,902  83 Linux
/dev/sda2             979,965 1,250,258,624 1,249,278,660   5 Extended
/dev/sda5             980,028     3,903,794     2,923,767  fd Linux raid autodetect
/dev/sda6           3,903,858 1,250,258,624 1,246,354,767  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002eadf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   5 Extended
/dev/sdb5                 126     3,903,794     3,903,669  fd Linux raid autodetect
/dev/sdb6           3,903,858 1,250,258,624 1,246,354,767  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022dba

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,250,258,624 1,250,258,562   5 Extended
/dev/sdc5                 126     3,903,794     3,903,669  fd Linux raid autodetect
/dev/sdc6           3,903,858 1,250,258,624 1,246,354,767  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00048ccf

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,250,258,624 1,250,258,562   5 Extended
/dev/sdd5                 126     3,903,794     3,903,669  fd Linux raid autodetect
/dev/sdd6           3,903,858 1,250,258,624 1,246,354,767  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c19f

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32     1,981,439     1,981,408   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6e35a059-9729-41d5-a3a9-970bc7faa0ee" TYPE="ext3" 
/dev/sda5: UUID="284fc2ed-4437-1111-c8ea-86731f3aab13" TYPE="linux_raid_member" 
/dev/sda6: UUID="5251ef3e-9e33-f220-4e7e-1833d10d6c34" TYPE="linux_raid_member" 
/dev/sdb5: UUID="284fc2ed-4437-1111-c8ea-86731f3aab13" TYPE="linux_raid_member" 
/dev/sdb6: UUID="5251ef3e-9e33-f220-4e7e-1833d10d6c34" TYPE="linux_raid_member" 
/dev/sdc5: UUID="284fc2ed-4437-1111-c8ea-86731f3aab13" TYPE="linux_raid_member" 
/dev/sdc6: UUID="5251ef3e-9e33-f220-4e7e-1833d10d6c34" TYPE="linux_raid_member" 
/dev/sdd5: UUID="284fc2ed-4437-1111-c8ea-86731f3aab13" TYPE="linux_raid_member" 
/dev/sdd6: UUID="5251ef3e-9e33-f220-4e7e-1833d10d6c34" TYPE="linux_raid_member" 
/dev/sde1: LABEL="FEDORA" UUID="4088-F1B3" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sde1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot type ext3 (rw)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root=(md1)
search --no-floppy --fs-uuid --set 331ea98b-2649-4520-ba53-7a03ebee7e5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-16-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro   quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-16-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro single 
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-14-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-14-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-16-generic
```
[B]
@lmarmisa[/B]

Which partition is sdXY?  I've got a RAID5 array stretched across 4 disks with the / partition on it.

---

### Post by lmarmisa on 2009-12-23
> **Leppie said:**
> this should actually be:
```
$dd if=/dev/sda of=/home/mbr.old **_bs=446_** count=1
```

I think that bs=440 is also good:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Leppie on 2009-12-23
> **lmarmisa said:**
> Try this modified script:

```

sudo mount /dev/sdXY /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

```

it's not really a script, just a couple of commands. anyways, /mnt/boot needs to be created first:
```
$sudo mount /dev/sdXY /mnt  ##change /dev/sdXY to the location of your raid unit
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot
$sudo grub-install --root-directory=/mnt /dev/sda
```

if the last command comes back with any errors, try adding the --recheck option:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda 
```

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> 
```
$sudo mount /dev/sdXY /mnt  ##change /dev/sdXY to the location of your raid unit
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot
$sudo grub-install --root-directory=/mnt /dev/sda
```



I'm not certain what you mean by the location of the raid unit, there are 4 partitions across 4 disks, which partition is the one I want to mount, or do I need to specify something else?

---

### Post by Leppie on 2009-12-23
I see you're using a fedora livecd, does this version of fedora use grub legacy or grub2? the instructions in the previous post only work if grub2 is already present on the livecd.

> **Leppie said:**
> ```
$sudo mount /dev/sdXY /mnt  ##change /dev/sdXY to the location of your raid unit
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot
$sudo grub-install --root-directory=/mnt /dev/sda
```

i'd suggest you use the karmic livecd (if you still have it around).

the grub.cfg has the wrong reference to your linux boot partition. it's now referring to UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c (not sure what partition this is as the script does not show this reference in other places), which should be UUID=6e35a059-9729-41d5-a3a9-970bc7faa0ee

try running the commands using a karmic live cd, this should correct the problem.

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> I'm not certain what you mean by the location of the raid unit, there are 4 partitions across 4 disks, which partition is the one I want to mount, or do I need to specify something else?

aren't the 4 partitions part of 1 raid unit? or are those 4 different raids?

---

### Post by Leppie on 2009-12-23
to mount the raid unit, use /dev/md0
```
$sudo mount /dev/md0 /mnt
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot
$sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> I see you're using a fedora livecd, does this version of fedora use grub legacy or grub2? the instructions in the previous post only work if grub2 is already present on the livecd.



i'd suggest you use the karmic livecd (if you still have it around).

It is a Karmic LiveCD, 32 bit, I installed the system with a 64 bit alternate Karmic CD.  Fedora comes from the fact that I'm using a live USB, created from the Ubuntu USB startup creator, which has previously been used with the Fedora one for Windows, which changed the volume label, and I haven't got round to changing it back.



> aren't the 4 partitions part of 1 raid unit? or are those 4 different raids?
There are two RAID partitions, the big one at sdX6 is a RAID5 for storage, the smaller one at sdX5 is RAID0 for swap (I know you don't strictly need to do that, but I thought it might be easier).

> the grub.cfg has the wrong reference to your linux boot partition. it's now referring to UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c (not sure what partition this is as the script does not show this reference in other places), which should be UUID=6e35a059-9729-41d5-a3a9-970bc7faa0ee
Can I change this by hand?

Sorry for being a bit thick at this...

Thanks,
Tim

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> to mount the raid unit, use /dev/md0
```
$sudo mount /dev/md0 /mnt
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot
$sudo grub-install --root-directory=/mnt /dev/sda
```

How can I check which array md0 refers to, as I think that md0 is my SWAP array.

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> It is a Karmic LiveCD, 32 bit, I installed the system with a 64 bit alternate Karmic CD.  Fedora comes from the fact that I'm using a live USB,
well, as long as it has grub2, it's good to use.

> **timbim said:**
> There are two RAID partitions, the big one at sdX6 is a RAID5 for storage, the smaller one at sdX5 is RAID0 for swap (I know you don't strictly need to do that, but I thought it might be easier).
so on which raid5 is your root installed (at least, i read in an earlier post that one of your concerns is that you have / on a raid5 and /boot on sda1).

> **timbim said:**
> Can I change this by hand?
you could change it by hand, but it's better to have the scripts do it. if you're sure what you're doing, you can just edit you're grub.cfg.

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> well, as long as it has grub2, it's good to use.
It does.


> **Leppie said:**
> so on which raid5 is your root installed (at least, i read in an earlier post that one of your concerns is that you have / on a raid5 and /boot on sda1).
That is correct, but /dev/md0 (and any other /dev/mdX) doesn't exist, which is worrying.


> **Leppie said:**
> you could change it by hand, but it's better to have the scripts do it. if you're sure what you're doing, you can just edit you're grub.cfg.Sounds like a job for a script then.

Looks like I'll be fine once I can mount /, but that's proving a little difficult at the moment.

---

### Post by Leppie on 2009-12-23
> **lmarmisa said:**
> I think that bs=440 is also good:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

from the same page:
> MBR, total size: **446** + 64 + 2 =	512

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> That is correct, but /dev/md0 (and any other /dev/mdX) doesn't exist, which is worrying.

what is the location of the raid5 unit hosting your root? if you want to use the commands i provided earlier, you will need to mount that raid unit. otherwise, just edit grub.cfg. just copy and paste the uuid reference (and just substitute the first one as a test).

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> what is the location of the raid5 unit hosting your root?What do you mean by that?  Is there a way to find out?

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> What do you mean by that?  Is there a way to find out?

how did you add it to your system? or was it already there when you installed linux on it for the 1st time?

---

### Post by timbim on 2009-12-23
I created them in them in the alternate install CD for karmic.

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> I created them in them in the alternate install CD for karmic.

well, since you don't know how the raid5 unit is mounted (and unfortunately i'm no expert either) try just editing the grub.cfg file for the 1st ubuntu entry.
once you're in the system you can check other things.



try starting the mdadm service:
```
mdadm --assemble --scan
```

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> 
try starting the mdadm service:
```
mdadm --assemble --scan
```

```
ubuntu@ubuntu:~$ mdadm --assemble --scan
mdadm: failed to create /dev/md0
mdadm: failed to create /dev/md1

```

Confirms that md0 and md1 exist, I suppose.

---

### Post by Leppie on 2009-12-23
well, then try modifying the first ubuntu entry manually.

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> well, then try modifying the first ubuntu entry manually.
So I'll edit grub.cfg, despite the big warning saying not to edit it.

Sounds like a plan!

```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	**linux	/vmlinuz-2.6.31-16-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro   quiet splash**
	initrd	/initrd.img-2.6.31-16-generic
```

I'm assuming the bold line's the offending one, and should be replaced with UUID=6e35a059-9729-41d5-a3a9-970bc7faa0ee

---

### Post by Leppie on 2009-12-23
yes, that's the one.
just change the "UUID=" part to the correct reference (UUID=6e35a059-9729-41d5-a3a9-970bc7faa0ee)

---

### Post by timbim on 2009-12-23
Won't let me save the file, despite the fact I gedited it as sudo.  Not helpful.

Gedit says:
> **Could not save the file /mnt/boot/grub/grub.cfg.**
You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.

Any ideas?

---

### Post by Leppie on 2009-12-23
unmount the boot partition:
```
$sudo umount /mnt/boot
```

mount with read/write permissions:
```
$sudo mount -w /dev/sda1 /mnt/boot
```

---

### Post by lmarmisa on 2009-12-23
The grub.cfg file is not editable. The standard way to update it is by means of the **sudo update-grub** command.

```

lmarmisa@UBUNTU910ENG:~$ ls -l /boot/grub/grub.cfg 
-r--r--r-- 1 root root 3536 2009-12-20 11:49 /boot/grub/grub.cfg

```

---

### Post by Leppie on 2009-12-23
> **lmarmisa said:**
> The grub.cfg file is not editable. The standard way to update it is by means of the **sudo update-grub** command.

the error message is:
> Could not save the file /mnt/boot/grub/grub.cfg.
You are trying to save the file on a **read-only disk**. Please check that you typed the location correctly and try again.
i've edited grub.cfg with no problems before.

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> unmount the boot partition:
```
$sudo umount /mnt/boot
```

mount with read/write permissions:
```
$sudo mount -w /dev/sda1 /mnt/boot
```Not working.  Still giving the same errors.

Hope I'm not going to have to attack it with something that really doesn't care what it's editing, such as SysRescCD...

---

### Post by lmarmisa on 2009-12-23
If you want to add write permission to the grub.cfg file, type this command

```

sudo chmod +w /mnt/boot/grub/grub.cfg

```

---

### Post by timbim on 2009-12-23
File edited, but no joy.  Still not booting normally.

However, I have got mdadm started, I needed to run it as root in order to create /dev/md0 and /dev/md1.

Looks like the HOWTO might help from here.

EDIT:  In the HOWTO, the first method instructs```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```In this case, would X be "a"?  It's slightly  confusing in the HOWTO, so I'm not sure what to put.

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> EDIT:  In the HOWTO, the first method instructs```
sudo grub-install --root-directory=/mnt/ /dev/sdX
```In this case, would X be "a"?  It's slightly  confusing in the HOWTO, so I'm not sure what to put.

yes, /dev/sda points to the mbr of that disk in this case.

---

### Post by Leppie on 2009-12-23
> **lmarmisa said:**
> If you want to add write permission to the grub.cfg file, type this command

```

sudo chmod +w /mnt/boot/grub/grub.cfg

```

i don't think it's a good idea to change the file permissions of the grub.cfg file. modify it as root, this will allow you to save it even though it's read-only.

don't forget to set file-permissions back to read-only.

---

### Post by timbim on 2009-12-23
Right, I issued```
sudo grub-install --root-directory=/mnt/ /dev/sda
```That didn't have the desired effect, although now the system gets to a grub command line on booting, and my live USB's broken, now reinstalling.  Any ideas what to do now?

---

### Post by Leppie on 2009-12-23
well, the grub prompt is a good sign.
at the grub prompt do the following:
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro		
initrd /initrd.img		
boot
```

when booted into the system, issue this command:
```
$sudo update-grub
```

and if you want you can also issue the following command:
```
$sudo grub-install --recheck /dev/sda1
```

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> well, the grub prompt is a good sign.
at the grub prompt do the following:
```
set root=(hd0,1)
**linux /vmlinuz root=/dev/sda1 ro		**
initrd /initrd.img		
boot
```
File not found on that command.

And I didn't put vmlinux, at least not the second time round.

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> File not found on that command.

And I didn't put vmlinux, at least not the second time round.

it's vmlinu**_z_** and not vmlinu**_x_** ;)

---

### Post by timbim on 2009-12-23
Still not found...

---

### Post by Leppie on 2009-12-23
could you post your current grub.cfg?

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> could you post your current grub.cfg?


**grub.cfg**
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod raid
insmod raid5rec
insmod mdraid
insmod ext2
set root=(md1)
search --no-floppy --fs-uuid --set 331ea98b-2649-4520-ba53-7a03ebee7e5c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-16-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro   quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-16-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro single 
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-14-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6e35a059-9729-41d5-a3a9-970bc7faa0ee
	linux	/vmlinuz-2.6.31-14-generic root=UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by Leppie on 2009-12-23
this one is the same as the one probed before.
try renaming it:
```
$sudo mv /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.old
```

then run:
```
$sudo grub-mkconfig
```

and check that UUID=331ea98b-2649-4520-ba53-7a03ebee7e5c is no longer being used.

could you also post your /etc/fstab (i didn't see it in the results of meierfra's script).

---

### Post by timbim on 2009-12-23
> **Leppie said:**
> this one is the same as the one probed before.
try renaming it:
```
$sudo mv /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.old
```


Since when I edited it manually, nothing happened, I changed it back before I forgot about it.  I'm working on the other bits, things going a little bit wrong at my end at the moment.

How do you know so much about GRUB anyway?

Thanks,
Tim

---

### Post by timbim on 2009-12-23
**/etc/fstab**
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```



```
$sudo grub-mkconfig
```Fails, saying > grub-probe: error: cannot find a device for /.


---

### Post by Leppie on 2009-12-23
> **timbim said:**
> How do you know so much about GRUB anyway?

when lilo was still around, i could do about anything i wanted with it.
then recently i tried installing systems with grub2, but ran into some issues. i started reading the forums, manuals, blogs, etc., then help out here and there ;)

---

### Post by Leppie on 2009-12-23
> **timbim said:**
> **/etc/fstab**
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```



```
$sudo grub-mkconfig
```Fails, saying

it looks like you haven't mounted the raid5 unit hosting your root partition. all the instructions where grub commands are run (like "sudo grub-mkconfig"), require you to have the root partition mounted.

---

### Post by Leppie on 2009-12-23
So, with the whole sequence:
```
$sudo mdadm --assemble --scan
$sudo mount /dev/md0 /mnt  ##mount the raid5 unit
$sudo mkdir /mnt/boot
$sudo mount /dev/sda1 /mnt/boot  ##mount /boot partition
$sudo update-grub  ##create grub.cfg (grub is already installed in the mbr)
```

---

### Post by timbim on 2009-12-24
Problem may be coming from the fact that /boot exists on the / array as well as on the /boot partition.  This appears to be causing problems as when I mount /dev/sda1 first, /dev/md1 doesn't mount (or at least it doesn't show up in /mnt, it claims it is already mounted).  The reverse is true if I mount them in the reverse order.

Any ideas?

---

### Post by Leppie on 2009-12-24
that would be a logical explanation. i already thought that the UUID in your grub.cfg is one of the raid volumes (as it doesn't show up in the partitions list).
try mounting one of the raid volumes and check for the presence of a boot folder on it. if there is, change to the parent directory (e.g. if it is in /mnt/boot, change to /mnt) and delete it like this:
```
$sudo rm -rf boot
```
careful with this command though, it will delete all contents in that folder.
once assured it doesn't contain the boot folder anymore, umount it and mount the next raid volume and check and remove if applicable the same way. then mount the raid volume containing / to /mnt and  /dev/sda1 to /mnt/boot and execute the command to regenerate grub.cfg.

---

### Post by timbim on 2009-12-24
Already tried deleting the /boot on the raid5 array, and then mounting as suggested.  The update-grub command gives ```
grub-probe: error: cannot find a device for /.
```Does this require a ```
sudo chroot /mnt
```, and if so, what does all the rest of the mounting achieve?

---

### Post by Leppie on 2009-12-24
chroot changes the root of the filesystem to the indicated folder. like this, during grub installation information is retrieved from your actual install and not from the livecd. the other mounts are necessary because those parts contain important information as well.

try this:
```
sudo mkdir -p /mnt/temp/boot
sudo mdadm --assemble --scan
sudo mount /dev/md0 /mnt/temp  ##assuming the root is on this volume, if not mount the other one
sudo mount /dev/sda1 /mnt/temp/boot
sudo mount -o bind /proc /mnt/temp/proc
sudo mount -o bind /dev /mnt/temp/dev
sudo mount -o bind /dev/pts /mnt/temp/dev/pts
sudo mount -o bind /sys /mnt/temp/sys
sudo chroot /mnt/temp /bin/bash
sudo update-grub
```

---

### Post by timbim on 2009-12-24
To clear up, where in this process do I need to mount /dev/sda1?  Given that mdadm has already sucessfully assembled, and will continue to do so with my liveusb, could you clarify this in the command order.

Thanks,
Tim

---

### Post by Leppie on 2009-12-24
sorry, forgot that initially. updated the sequence.

---

### Post by timbim on 2009-12-24
```
sudo chroot /mnt/temp /bin/bash
```Still gives > chroot: cannot run command '/bin/bash': Exec format error

---

### Post by Leppie on 2009-12-24
> **timbim said:**
> ```
sudo chroot /mnt/temp /bin/bash
```Still gives

then try this instead:
```
$sudo chroot /mnt/temp /usr/sbin/update-grub
```

---

### Post by timbim on 2009-12-24
> **Leppie said:**
> then try this instead:
```
$sudo chroot /mnt/temp /usr/sbin/update-grub
```Same error...:(

---

### Post by Leppie on 2009-12-24
are you sure you mounted the root of your normal ubuntu filesystem?

---

### Post by timbim on 2009-12-24
> **Leppie said:**
> are you sure you mounted the root of your normal ubuntu filesystem?

Yes.  I'm beginning to think I might be better off deleting it all and starting again...

---

### Post by Leppie on 2009-12-25
As I wrote previously, I'm no expert on raid units (unfortunately).
Anyways, is there a specific reason you put the root system on a raid5? I understand people would like something like that for their data, but the system as well?

What commands do you use to mount the raid units? And once mounted, can you browse them and is /bin/bash on one of them?

---

