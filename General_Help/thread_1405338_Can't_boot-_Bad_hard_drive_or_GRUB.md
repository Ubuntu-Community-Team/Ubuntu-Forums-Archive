---
title: "Can't boot- Bad hard drive? or GRUB?"
date: 2010-02-12
forum: General Help
---

### Post by plaine on 2010-02-12
I've been scouring the forums and Google for 2 days now and am not sure which track I should follow with my problem, because the GRUB path doesn't seem to be working, nor the fsck.  I'd appreciate any insight anyone can provide, as I feel I'm spinning my wheels at this stage.

A few days ago, I was transferring files from my Ubuntu server via SFTP to my laptop across my local network.  All of a sudden, the transfer quit in the middle of transferring a file and since then, I was unable to FTP or SSH in to the server.  I hooked up a monitor to see what was going on and there was only a black screen, so I powered off the server and powered back on.

While booting, the Ubuntu logo screen initially appears, but then goes to black and error messages come up, asking me if I wish to start the degraded RAID.  "Gave up waiting for root device" is the message I get and it tells me that /dev/md2 does not exist and drops me to a initramfs shell.  When I try to start in degraded RAID, it tells me:
mdadm: create user root not found
mdadm: create group disk not found
[49.702561] raid5: failed to run raid set md2
mdadm: failed to run RUN_ARRAY /dev/md2: Input/output error
mdadm: not enough devices to start the array

I have 4 hard drives in the server, configured as RAID 5.  
I boot from a Live CD and have a look at the discs.  All are said to be healthy, except for the 4th which is said to have some bad sectors.

I'm unable to access (or don't properly know how to access) the /boot/grub/menu.1st file to change the root delay parameter, which is what I thought I would try first.  

Can anyone lend me any assistance?  Thank you.

---

### Post by IcarusR on 2010-02-12
To edit menu.lst boot from live cd, mount failed / partition, cd to mounted / partition & type..
```
sudo gedit /boot/grub/menu.lst
```

Note it lower case lst not 1st

I do not think changing the delay will resolve this, but no harm in trying.
That said I have no better ideas, not familiar with boot raids.

Good luck.

---

### Post by plaine on 2010-02-12
Do you think this is more a disk corruption problem?  Since this happened mid-file transfer, I wasn't sold on the idea that its GRUB either, but I'm a novice.  I wasn't updating anything, I didn't reboot anything, it just stopped working mid-stream.  If you don't think its GRUB, any advice on what else I should try?  Thanks for your response.

---

### Post by IcarusR on 2010-02-13
Googling I found that people type 'exit' at the intramfs shell & they continue to boot OK.
They then edit /boot/grub/menu.lst & add 'rootdelay=90' to kernel options. like this

kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=a9d96802-b2f1-4a49-8fd5-a15ac8961217 [COLOR="Red"]rootdelay=90[/COLOR] quiet splash

I have seen people using 40, 90 & 120 I guess it is question of experimenting.

If you can not boot at all, then boot from 'live cd' mount drive & then edit menu.lst

---

### Post by diosney on 2010-02-22
> **IcarusR said:**
> Googling I found that people type 'exit' at the intramfs shell & they continue to boot OK.
They then edit /boot/grub/menu.lst & add 'rootdelay=90' to kernel options. like this

kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=a9d96802-b2f1-4a49-8fd5-a15ac8961217 [COLOR=Red]rootdelay=90[/COLOR] quiet splash

I have seen people using 40, 90 & 120 I guess it is question of experimenting.

If you can not boot at all, then boot from 'live cd' mount drive & then edit menu.lst

Thanks a lot IcarusR!!

That simple solution worked very well for me!!

---

### Post by logan_2k6 on 2010-05-02
Hi,

I've been trying Kubuntu 10.04 (so called final release) from wubi install. But couldn't get too far since it seems that after each reboot for some reason my hard drives gets new device number.
For example 1 reboot i have my hard drive as /dev/sda1 and next reboot i get /dev/sdc1 and it keep switching around. I don't change absolutly nothing. I just type reboot in console (cause i get that message with rootdelay bla bla) and next reboot i have the next inline identifier for my hard drive.
Any ideas how to fix this?

---

### Post by WorMzy on 2010-05-02
use ```
sudo blkid
``` to get the UUID for the partitions you want to mount, and edit etc/fstab accordingly. UUIDs do not change, even if the order of disks is changed. So, for example "/dev/sda1" in fstab might become "UUID=097bbeed-7751-448f-bfb5-01f9bc9d76ac".

---

### Post by logan_2k6 on 2010-05-03
Hi,
Thank you for quick answer.
Since last night i have to reinstall kubuntu cause of ati drivers crash my kubuntu. Now of course i have another device in Grub.
Now I did that command but the "problem" is that i don't have any /dev in fstab for my root device
My fstab looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

(I'm a bit confuse which one configuration file is first in line when system boot up fstab or grub commands)

and the results of blkid are

/dev/loop0: UUID="06dc23c1-23fc-4cbd-b989-a2c7887bccb5" TYPE="ext4" 
/dev/sda1: UUID="4CA49805A497EFA6" TYPE="ntfs" 
/dev/sdb1: UUID="9AA498EDA498CD5F" TYPE="ntfs" 
/dev/sdc1: LABEL="System Reserved" UUID="10400A4F400A3BCA" TYPE="ntfs" 
/dev/sdc2: UUID="48F610D5F610C55A" TYPE="ntfs" 
/dev/sdd1: LABEL="WD 04" UUID="F43A846E3A842FA2" TYPE="ntfs" 
/dev/sde1: UUID="6834FF2034FEF044" TYPE="ntfs" 
/dev/sdf1: UUID="30BE8B42BE8B0018" TYPE="ntfs" 
/dev/sdg1: LABEL="WD 03" UUID="F8C0C4ABC0C47184" TYPE="ntfs" 
/dev/sdh1: LABEL="WD_02" UUID="4430D18230D17AFE" TYPE="ntfs" 
/dev/sdi1: LABEL="New Volume" UUID="2CCA7FD3CA7F9832" TYPE="ntfs" 

(lucky me i have only 1 drive with 2 partition (the one with windows/kubuntu))

How should my lines in fstab should be? my hard drive with kubuntu is on /dev/sdc2,

Now another question I have is: how can i make update-grub to update my menu list base on UUIDs and not on /dev

---

### Post by WorMzy on 2010-05-03
Oh.. are you using wubu?

I'm not familiar with that, but it looks like your fstab is fine. You could try running sudo update-grub, but I don't use grub2, so I'm not sure if this will help.

---

### Post by logan_2k6 on 2010-05-03
Yeap i use Wubi.
sudo update-grup makes /dev like menu list.
so i guess there is no way to make update grub with UUID. i'll have to manually change the menu list. but i'm not sure how to change /dev and hd(blabla,blabla) in uuid.
do i just change 'hd(bla,bla)' in UUID='bla bla' and /dev/blabla in UUID='blabla' ?
:)

---

### Post by WorMzy on 2010-05-03
Does it make a menu.lst? Because that would mean you have grub legacy, which I do know about.

If you do have /boot/grub/menu.lst, can you post what it says here please? I'll advise you how to proceed.

---

### Post by logan_2k6 on 2010-05-04
Ok so this is my grub.cfg file


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 48f610d5f610c55a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdc2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 48f610d5f610c55a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdc2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10400a4f400a3bca
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ### 








The hd(2,2) and /dev/sdc2 change according to whatever i manage to change in grub menu during boot up. As i said before these devices keep switching every reboot. So if i reboot and my boot drive is hd(0,2) = /dev/sda2 then when i run update-grup ill get hd(0,2) and /dev/sda2 instead of hd(2,2) /dev/sdc2...and again after another boot if i run again update-grub then ill have 2,2 /sdc2 and again and again and again .....and again....

---

