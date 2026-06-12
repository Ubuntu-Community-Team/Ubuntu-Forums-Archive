---
title: "&quot;No such partition&quot; error from grub-rescue after install on 9.10"
date: 2010-01-13
forum: General Help
---

### Post by InMyHumbleOpinion on 2010-01-13
This is a new install attempted for a dual boot.  PIII 500MHz, 2G RAM, single 100+ SCSI HD, trying to keep Windows XP.
 

Everything is fine running Ubuntu from the install DVD.  And even if there are any errors from the install, the file system is present on the hard drive, as I can access it when booted from the install DVD.
 

Boot up goes into grub-rescue with the "No such partition" message.  ls command returns "(hd0), (hd0,1), and fd(0)".
 

The drive is Western Digital WDC1600 BB-00HTA0. After doing some post install adjustments with gparted, the partitions look as follows:


partition-file system-total space-flags
/dev/sda1-nfts-32.056G-boot
/dev/sda2-extended-116.99G-lba
    /dev/sda3-ext4-114.99G-(none)
    /dev/sda4-linux-swap-2G-(none)
approx 7.8M free space
 
If I'm reading the rescue list right, it's only recognizing the Windows XP partition, which of course doesn't have grub, and the whole thing is stalled.  I've tried to set root and boot directories (per the official documents) to (hd0,3), but it doesn't recognize that partition.
 
I've now tried manually flagging the sda3 with boot, but got no change from that.  So what should I do from here?

---

### Post by InMyHumbleOpinion on 2010-01-14
This is a new install attempted for a dual boot.  PIII 500MHz, 2G RAM, single 100+ SCSI HD, trying to keep Windows XP.
 

Everything is fine running Ubuntu from the install DVD. And even if there are any errors from the install, the file system is present on the hard drive, as I can access it when booted from the install DVD.
 

Boot up goes into grub-rescue with the "No such partition" message.  ls command returns "(hd0), (hd0,1), and fd(0)".
 

The drive is Western Digital WDC1600 BB-00HTA0. After doing some post install adjustments with gparted, the partitions look as follows:


partition-file system-total space-flags
/dev/sda1-nfts-32.056G-boot
/dev/sda2-extended-116.99G-lba
    /dev/sda3-ext4-114.99G-(none)
    /dev/sda4-linux-swap-2G-(none)
approx 7.8M free space
 
If I'm reading the rescue list right, it's only recognizing the Windows XP partition, which of course doesn't have grub, and the whole thing is stalled. I've tried to set root and boot directories (per the official documents) to (hd0,3), but it doesn't recognize that partition.
 
I've now tried manually flagging the sda3 with boot, but got no change from that.  So what should I do from here?

---

### Post by David_Melb on 2010-01-14
UBUNTU 9.10
I had a similar problem where I was unable to boot into XP.
I had two hard disks installed IDE and SATA the boot was on sadata.  The IDE also had been marked as boot which confused grub.  I reformatted my IDE to eliminate the boot information. I checked and ensured that I had both UBUNTU and XP installed.
 
Found information that fixed the problem easily.  This information was well hidden the forum. 
In terminal mode check the disk Drives with
   sudo fdisk -l    (as in l for little)
 
In my case 
     sata was sdb
       /dev/sdb1 was the boot device HPFS/NTFS
       /dev/sdb2 had W95
       /dev/sdb6 had linux
       /dev/sdb7 had Linux Swap
 
NB Make sure ther is only one boot marked.
 
FIX 
In Terminal
   sudo grub-mkdevicemap
   sudo updat grub
 
Rebooted PC and checked that I was able to boot up in both systems.

---

### Post by InMyHumbleOpinion on 2010-01-14
Thank you for the response.  I tried what you suggested, including the dash in sudo update-grub command and got this return:

"grub-probe: error: cannot find a device for /."

I'm running Ubuntu from the CD and think it's trying to run the CD's grub.  I don't know how to get into the hd in terminal.

Strangely enough, I now notice that both the fdisk -l command and gparted show the linux file as sda 5 and the swap as sda6.  There are no sda3 or sda4.

Anything I'm missing here?

Update- I've found the directory onto the HD, it's /media/486f88f7-6d4a-4791-a34f-0df4025bd5f1.  But no recognized update-grub from there.  I also noticed that the fdisk command you suggested lists the extended partition as a 'Win95 ext'd (LBA)' system.  So I'm wondering if removing that flag on gparted might help things.

---

### Post by louieb on 2010-01-14
Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")and put the results.txt file in you next post.

---

### Post by InMyHumbleOpinion on 2010-01-14
I'm getting ready to go to work, and just checked the forum in the short time I have (the install in question is on a home computer).  That was enough time to download and run the application, but not to figure out anything from it.  Pardon if there something in the text that I would have recognized right off (though that's doubtful at this stage).  Output follows:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb29fc4fe

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    67,215,959    67,215,897   7 HPFS/NTFS
/dev/sda2          67,215,960   312,560,639   245,344,680   5 Extended
/dev/sda5    *     67,216,086   308,367,674   241,151,589  83 Linux
/dev/sda6         308,367,738   312,560,639     4,192,902  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="90980C15980BF88C" TYPE="ntfs" 
/dev/sda5: UUID="f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2" TYPE="ext4" 
/dev/sda6: UUID="19eb21d3-071e-47bc-8165-f56da00d6afb" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
signature(b29fc4fe)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 
signature(b29fc4fe)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 90980c15980bf88c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=19eb21d3-071e-47bc-8165-f56da00d6afb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  34.4GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.31-14-generic
  34.4GB: boot/vmlinuz-2.6.31-14-generic
  34.4GB: initrd.img
  34.4GB: vmlinuz

---

### Post by searchesend on 2010-01-14
Hello mate, I'm a complete newb but I just fixed the same problem using this guide here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I did
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit

...then I rebooted. 
Anyway, I hope this sorts it out for you

---

### Post by louieb on 2010-01-14
Don't see anything wrong with the setup. 

> tried manually flagging the sda3 with boot

Linux and GRUB does not care if the boot flag is set or not.  It should be set back to your windows partition. 

How old is the BIOS  - older BIOS versions could not see or boot anything past 33GB or so from the start of the drive. (Usually results in GRUB errror 18 - but not always). 
```

=================== sda5: Location of files loaded by Grub: 
  34.4GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
  34.4GB: boot/initrd.img-2.6.31-14-generic
  34.4GB: boot/vmlinuz-2.6.31-14-generic
  34.4GB: initrd.img
  34.4GB: vmlinuz 	

```

My best guess - Check the drive in BIOS setup and make sure the mode is set to LBA (logical block addressing)

---

### Post by InMyHumbleOpinion on 2010-01-14
Thank you.  I've done a bit more since the last post.  But I'll give that a try, and if it doesn't work, state the current, err, state then.  It definitely seems like a mounting problem- or at least that's one possibility for now read.

---

### Post by Leppie on 2010-01-14
with a little bit of luck you can boot from the rescue prompt:
```
normal
set root=(hd0,5)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sda4 ro		
initrd /initrd.img		
boot
```

---

### Post by InMyHumbleOpinion on 2010-01-14
So does this have any meaning:
 
"# / was on /dev/sda5 during installation
UUID=f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2 / ext4 _errors=remount-ro 0 1_"
 
I know the Bios is at least updated as of 2000, which doesn't say much.  I think I updated it again, but will check.  That should not be a problem though, asI had the drive divided into 3 partitions each over 40G when Windows XP was running and there was no problem there.
 
So you know, I had posted in the installation forum as well before you responded here.  The bit of advice from searchesend looks like a move in the right direction ([http://ubuntuforums.org/showthread.php?p=8666509&posted=1#post8666509](http://ubuntuforums.org/showthread.php?p=8666509&posted=1#post8666509)), so I'll be giving that a try and reporting, along with a more definite statement about the BIOss version/date.  If there's anything else you can think of, I am all ears, err, eyes.

---

### Post by cariboo on 2010-01-14
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by louieb on 2010-01-14
> The bit of advice from searchesend looks like a move in the right direction The suggestion he made is for GRUB legacy (used by Ubuntu in releases prior to 9.10) and is not applicable in your case.  Leppie in post #10 gives the correct commands for GRUB2.

> Windows XP was running and there was no problem there.Best guess is XP worked ok because its boot-loader and kernel are both within the 1st 33GB of the hard drive. That applies to IDE/PATA hard drives - you said the drive was SCSI - that could make a difference - haven't used SCSI so don't know.   

> I had posted in the installation forum as well before you responded hereThaks for the heads up. Double posting is confusing - Please use the report button - let the moderators know - and one of them will merge the two threads. - Get everybody on the same page.;)

---

### Post by Miljet on 2010-01-14
> "# / was on /dev/sda5 during installation
UUID=f97031c4-abbb-4f9f-b5ca-f3c9b4a65be2 / ext4 errors=remount-ro 0 1"

The part that you underlined does not indicate a mount problem. It is simply an option telling the computer that if an error occurs while mounting this partition to try remounting it as read only.

---

### Post by InMyHumbleOpinion on 2010-01-14
Sorry about the double post all.  I posted in one and when I got no answer tried what I thought might be a more pertinent forum after the fact.  Sorry for any confusion.

So I'll give Leppie's rec a try.  Wish me luck.

---

### Post by InMyHumbleOpinion on 2010-01-15
Some updates based on my attempts given the advice given here:

1)  I tried Leppie's advice and was shot down at the first command.  Normal would not do anything.

2)  I still tried Searchesend's advice just to see and, not surprisingly, it didn't work.  Hopefully it didn't muck anything up, but given that I have nothing vested that can be hurt by a repartitioning and reinstalling, it's relatively moot.

3)  I checked the Bios for the HD setting and all such devices are set to auto.  When the bios registers the HD and I enter that section, switching from auto to HD w/the lbc opion gives all the same parameters that auto does.  So I don't think there is a problem there and, honestly, I don't want to muck with it.

4) Possibly, more interesting is that I found that there is nothing hooked up as the primary master device.  This HD is hooked up as the primary slave and the DVD R/W is the secondary master.

5)  I looked up the Bios revision on the ASUS page and found that the current version I have is 2000 and the second to last version available.  The most recent version is 2004, however they describe it as "most recent beta".  Until I run out of all other options, I'm passing on that.


Is there a grub 2 version along the lines of what Seachesend suggested?  Other options I'm considering are to reinstall, but partitioning ubuntu onto a standard instead of a logical partition.  I know it shouldn't make a difference, but it's something to try.

I also don't know how the fact that it's a SCSI drive would affect it's ability to boot from beyond 33.4.  Let me know if any of the above information presents a new light if there is any other advice.

---

### Post by presence1960 on 2010-01-15
> **InMyHumbleOpinion said:**
> This is a new install attempted for a dual boot.  PIII 500MHz, 2G RAM, single 100+ SCSI HD, trying to keep Windows XP.
 

Everything is fine running Ubuntu from the install DVD.  **_And even if there are any errors from the install_**, the file system is present on the hard drive, as I can access it when booted from the install DVD.
 

Boot up goes into grub-rescue with the "No such partition" message.  ls command returns "(hd0), (hd0,1), and fd(0)".
 

The drive is Western Digital WDC1600 BB-00HTA0. After doing some post install adjustments with gparted, the partitions look as follows:


partition-file system-total space-flags
/dev/sda1-nfts-32.056G-boot
/dev/sda2-extended-116.99G-lba
    /dev/sda3-ext4-114.99G-(none)
    /dev/sda4-linux-swap-2G-(none)
approx 7.8M free space
 
If I'm reading the rescue list right, it's only recognizing the Windows XP partition, which of course doesn't have grub, and the whole thing is stalled.  **_I've tried to set root and boot directories (per the official documents) to (hd0,3)_**, but it doesn't recognize that partition.
 
I've now tried manually flagging the sda3 with boot, but got no change from that.  So what should I do from here?

Why would you say "even if there were errors during the install"? Did you have any ? If so your install may be faulty

Your Ubuntu root is (hd0,5)- see the script output. In GRUB Legacy it would be (hd0,4).

I would boot the Live CD and choose "check disk for defects" at the menu. You should have done this first anyway. If the disk has any errors your ubuntu install can not be expected to function properly. If the disk is found to be OK then do this:

Even though GRUB is installed and pointing to sda5 as it should why don't you reinstall GRUB? It can't hurt and see what happens. Boot the 9.10 Live Cd & choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```This will mount your Ubuntu / partition. Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB back to MBR.

Reboot without the Live Cd and see what happens. If you can boot into Ubuntu, open a terminal and run ```
sudo update-grub
```
Then reboot & try booting into windows.

If your BIOS can not read past 33 GB as Louieb points out you are going to have to create a separate /boot partition within the first 33 GB of your hard disk or GRUB will never get your OSs to boot because the BIOS is unable to read the files necessary to boot. Or update BIOS.

---

### Post by InMyHumbleOpinion on 2010-01-15
I said "even if there were errors during the install" because, even though the graphic install makes it look easy, I recognize that this is a complicated (behind the scenes as it were), if automated, process.  Since I can't boot it up, I can't test it.  I wasn't there were errors.  I saw none mentioned, but for now, I don't know either way.
 
I did run the test the check disk for defects first thing, and none were found.
 
I tried the code you gave presence1960.  Unfortunately, no joy from that.  I think you're right about my remaining options.  I split them to, 1) update the BIOS, 2) repartition so /boot and Windows are within the first 33 Gigs of the harddrive, and always 3) give up on dual boot and just repartition so it's only Ubuntu.
 
One side question I have.  On the installs so far, near the end, I have three options that are (paraphrased), 1) Log in automatically (save log in and password), 2) require log in and password, 3) same as 2, but decrypt /home folder.
 
Now I belive it was /home folder, but I am certain the word decrypt or decryption was used, not encrypt or encryption.  Does this mean that the second option encrypts the folder and it's contents and the third doesn't?
 
Hope to have Ubuntu running, as sole OS or dual boot by tomorrow, if not tonight.

---

### Post by Leppie on 2010-01-15
sometimes instead of normal "insmod /boot/grub/normal.mod" (without the quotes) is working:
```
insmod /boot/grub/normal.mod
set root=(hd0,5)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

---

### Post by InMyHumbleOpinion on 2010-01-15
I checked in one last time before heading home.  I'm doubting it will work at this point, but no harm in trying.  I'll let you know.

---

### Post by InMyHumbleOpinion on 2010-01-17
Finally have it installed after trying many partition setups and multiple installs.

In the end, for whatever reason, I think the root partition with boot had to be in the first partition, following the MBR.  That's what ended up working.  Just in case, I also kept it to under 33 gigs of space.  I post this as the Update Manager is downloading available package info.

Thank you all for your help.  It looks like my old hardware is spotty when it comes to some of the things Ubuntu can otherwise do, but it looks like it is working now.  After all the time before and most of the day today, I am quite happy.  Thank you again.

---

