---
title: "Dell Mini is completely fuabr'd"
date: 2010-12-12
forum: General Help
---

### Post by vegetopia on 2010-12-12
You'll have to excuse my gross incompetence and ignorance with everything Linux related and if you dare, hold my hand through this process, but I'm in need of some help and this seems like a great place to try and get some.

I have a Dell Mini 10v that I previously installed Ubuntu 10.04 to without a problem. After I figured out how to do little things like enable Java, I was able to run the one program I installed ubuntu for in the first place. Everything was great, life was beautiful, my program ran without giving me the constant BSOD that was the case when I was running it on Windows...

That is until yesterday, when I booted up the laptop and interrupted the boot process by holding down the power button to make it shut off (I was having power problems and didn't know the computer was booting until it was too late). Now it won't boot and gives me an error akin to this (pulled from a web search):

> [LEFT][COLOR=#000000]mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _


Read more: [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#ixzz17xc8jUSu](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#ixzz17xc8jUSu)[/COLOR][/LEFT]

so naturally I prepared a USB drive with ubuntu and tried to boot to it to run Terminal. Well, that doesn't work either. The BIOS sees the usb drive and lets me choose to boot to it, but then it hangs at the purple ubuntu screen and I can get nowhere with it.

I also tried booting to a osx usb drive and using terminal included there, but the commands don't translate and another web search I tried for similar help yielded no positive results.

Is there anything I can do? at this point I would just start over and lose my data, but I can't even do that since I can't get it to boot to the USB. And yes, I tried the USB drive on another computer and it booted into Ubuntu just fine.

thanks in advance,
-Jamie

---

### Post by vegetopia on 2010-12-14
I'm getting the impression I'm out of luck here.

---

### Post by Quackers on 2010-12-14
What graphics card are you using?

---

### Post by vegetopia on 2010-12-14
Intel GMA 500, I believe.

---

### Post by Quackers on 2010-12-14
Boot from the Live usb and at the purple splash screen press any key. This will bring a different screen up. Press F6 on this screen and some boot options will appear on the right side.
Nomodeset is a commonly used one (but I think mainly for nvidia graphics card - but I could be wrong there).
i915 options are used for Intel graphics so either could be worth a try.
You may need to use all 6 to see which allows you to boot up fully.
Good luck :-)

---

### Post by vegetopia on 2010-12-14
no go, when the purple splash screen appears, the little red dots starting counting off and it hangs here. If I press esc (the only key that is responsive) it pulls me into a command window. The last thing listed there is 
> 
unable to open ' /dev/sda'

I cannot input any text at this point.

I really appreciate the help. keep it coming if you can. I'm on the verge of loading win7 on here, but would really like to stick with ubuntu and would really like to keep my data that i have on this netbook.

---

### Post by mmsmc on 2010-12-14
it sounds like you accidentally crashed your ubuntu system, when you get to the window that lets you choose which system to upload try the ubunty recovery one, and if that doesnt work we'll trouble shoot from there

---

### Post by vegetopia on 2010-12-14
When I choose the USB stick as my boot device in the BIOS, it brings me to the Ubuntu Installer Boot Menu. I have 6 options here:

1) Run Ubuntu from USB
2) Install Ubuntu
3) Test Memory
4) Boot from first hard disk
5) Advanced options (if you select this category, it is empty)
6) Help

that's all i have. If I run from usb, it hangs with the above error message. If I try to install, it hangs with the above error message. I think I'm cursed...

Is there another method of attempting to enter the recovery section?

---

### Post by mmsmc on 2010-12-14
I have 10.10 so the options may be different, let me research this talk to some friends and i'll get back to you ASAP, dont worry this can be resolved.

---

### Post by vegetopia on 2010-12-14
thanks man, I really appreciate it.

I just had a thought. I know I installed 10.04 (and that's also what I prepared my USB stick with), but perhaps I upgraded to 10.10 in one of the auto updates along the way? Is it possible that's why I can't launch ubuntu from the usb?

I'll try it, just for shits and giggles.

---

### Post by mmsmc on 2010-12-14
it is possible, can you boot from a live cd?

---

### Post by vegetopia on 2010-12-14
well, the netbook doesn't have an optical drive (and I don't have a usb dvd rom) so that's why I've been using the USB method. It's all I have available to me atm.

---

### Post by mmsmc on 2010-12-14
here this may help

This solution solved my problem as well on 10.04, boot failed and I didn't even make it to Grub.

I had the warning:

     Quote:
                                                 target filesystem doesn't have /sbin/init
No init found try passing init = bootarg                                 
While booted into the live CD for 10.04, my boot drive wouldn't mount giving me some error I forgot to write down (sorry).  

If anyone stumbles across this problem in the future, here's how to  start gparted fromthe live CD for those who'd like to use this method:

     Quote:
                                                 sudo gparted                                 
once there, you can select your hard disk from the drop down menu  at the upper right corner of the software.  As long as the  drive/partition you are interested in repairing is unmounted, you can  right click on it and select 'Check.'  This has the effect of checking  the disk and if possible, repairing any issues, (for those from the  windows world its much like chkdsk).

I drilled down into the 'Details' view of the Check and it showed the  exact same command that 9047boy used (except of course with my partition  name instead of his):

     Quote:
                                                 e2fsck -f -y -v /dev/sdb1                                 
Thanks a million 9047boy and I hope this helps others in the future!

-Adam

srry, just noticed your last post, you may need an external cd drive, but dont go out and buy one just yet, ill look some more
                                                                                                  [IMG]http://wwww.ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                             [[IMG]http://wwww.ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://wwww.ubuntuforums.org/report.php?p=9299508")                                                                                         [[IMG]http://wwww.ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://wwww.ubuntuforums.org/newreply.php?do=newreply&p=9299508")

---

### Post by vegetopia on 2010-12-14
SUCCESS! I was able to boot to the 10.10 usb drive!

I'm going to try the gpart method now.

---

### Post by mmsmc on 2010-12-14
cool,if you are succesful with that tell me how you did it so u can pass the information on to others with the same problem

---

### Post by vegetopia on 2010-12-14
ok, I'm in gparted and I select my primary partition which is /dev/sda1 and also contains the "boot" flag, right click > check > apply operation, but then I get an error message, basically telling me the that drive is in use and I can't check it.

Why is this? the drive shouldn't be in use, I'm booted to the USB drive right now ???

---

### Post by mmsmc on 2010-12-14
first of all, in your BIOS is it checked that the usb drive should be booted up first? if so this would cause this problem, if not you might need to go through the reinstallation process again(meaning you may have to take ubuntu 10.10 from your usb drive and put it on your comp)

---

### Post by vegetopia on 2010-12-14
I'm not quite sure I understand what you're asking. In my BIOS, my HD is set to be the first boot device, then the USB drive. I am currently booted to Ubuntu 10.10 on the USB drive (equivalent of a Live CD).

Once I am in the Ubuntu desktop from the USB drive, I am running gparted from terminal and I get the error that my internal HD is busy. I am unclear as to why that is since I am booted from the USB drive, not the internal drive.

Is there a way to unmount or otherwise make available the internal HD so that gparted may run the check?

---

### Post by Quackers on 2010-12-15
If you open a terminal what name is shown at the terminal prompt?

---

### Post by mmsmc on 2010-12-15
you may have to add a new partition, or replace the one you are on, try this website [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by vegetopia on 2010-12-15
> **Quackers said:**
> If you open a terminal what name is shown at the terminal prompt?

ubuntu@ubuntu:~$


I also tried going into hte Disk Utility and clicking on the drive, then clicking "check filesystem"

It says "error the daemon is inhibited"


here's another thought: If I go through the 10.10 install process and do not format the internal drive in the process, will it keep my data intact?

---

### Post by Quackers on 2010-12-15
I think it may be a good idea if you go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by vegetopia on 2010-12-15
it is currently "searching sda1 for information" how long should that take?

---

### Post by Quackers on 2010-12-15
A couple of seconds.
I suspect sda1 is deceased (or at least its file system).
The boot script might tell us.

---

### Post by vegetopia on 2010-12-15
well, it's been going on for well over a minute now...

---

### Post by vegetopia on 2010-12-15
while we're waiting, here's the error that gparted returned:

```
GParted 0.6.2
 Libparted 2.3
    **Check and repair file system (ext4) on /dev/sda1**  00:00:00    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 2048
end: 228483071
size: 228481024 (108.95 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )             ***e2fsck -f -y -v /dev/sda1***             [I]Filesystem mounted or opened exclusively by another program?
[/I]       [I]e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
[/I]             ========================================

```

---

### Post by vegetopia on 2010-12-15
any new suggestions for me to try?

If I re-install ubuntu 10.10 onto the internal HD, without formatting the drive, will my data remain intact?

---

### Post by mmsmc on 2010-12-15
if you reinstall ubuntu 10.10 over your ubuntu than all will b lost, if you dual boot by adding another partition than it will be fine

---

### Post by vegetopia on 2010-12-15
yeah that wont do me any good. i basically do have a dual boot now, by booting from the usb, and i still cant access my internal hd.

---

### Post by mmsmc on 2010-12-15
for now do that, i dont have much experience with your situation, for now i can keep looking and can maybe try and get an admin to help

---

### Post by sonatso on 2010-12-15
I may be wrong, but since you are booting from a USB, /dev/sda1 is probably the USB drive; check if there are any other disks on the system in /dev.

---

### Post by vegetopia on 2010-12-16
still looking for suggestions on how to access this drive. I would be very happy simply being able to navigate the drive and extract my data from it. No need to make it a working install again.

Is there a way I can do just that?

---

### Post by vegetopia on 2010-12-16
> **sonatso said:**
> I may be wrong, but since you are booting from a USB, /dev/sda1 is probably the USB drive; check if there are any other disks on the system in /dev.

thanks for the suggestion. /dev/sda1 is definitely the internal HD. My USB is only 1gb, and /dev/sda1 lists as 120gb, so I'm fairly confident that it is the correct drive.

---

### Post by vegetopia on 2010-12-16
quackers, where'd you go man?

---

### Post by pellgarlic on 2010-12-17
hi, can you do the following:

boot from your usb drive, then open a terminal and type the following 3 commands (one at a time), and paste the output here:

# fdisk -l
# dmesg | grep sd
# mount

---

### Post by vegetopia on 2010-12-17
> **pellgarlic said:**
> hi, can you do the following:

boot from your usb drive, then open a terminal and type the following 3 commands (one at a time), and paste the output here:

# fdisk -l
# dmesg | grep sd
# mount


absolutely! However, the mini is at home, so it won't be until after work. Thanks for the help.

---

### Post by vegetopia on 2010-12-17
went home for lunch...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aca4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114240512   83  Linux
/dev/sda2           14223       14594     2977793    5  Extended
/dev/sda5           14223       14594     2977792   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      976564    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(121, 148, 2)
/dev/sdb2             122         488     2939139   af  HFS / HFS+
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(121, 149, 1)
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(487, 124, 63)
```


```
ubuntu@ubuntu:~$ sudo dmesg | grep sd
[    6.442552] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    6.442659] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.442855] sd 0:0:0:0: [sda] Write Protect is off
[    6.442925] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.443032] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.443536]  sda: sda1 sda2 < sda5 >
[    6.508979] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.077173] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    8.078131] sd 2:0:0:0: [sdb] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
[    8.078617] sd 2:0:0:0: [sdb] Write Protect is off
[    8.078625] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    8.078630] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.080995] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.081025]  sdb: sdb1 sdb2
[    8.087228] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.087239] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.138140] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    8.145531] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[    9.331914] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    9.331927] EXT4-fs (sda1): write access will be enabled during recovery
[    9.401080] EXT4-fs warning (device sda1): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    9.401094] EXT4-fs warning (device sda1): ext4_clear_journal_err: Marking fs in need of filesystem check.
[   33.266343] Adding 2977788k swap on /dev/sda5.  Priority:-1 extents:1 across:2977788k
```


```
ubuntu@ubuntu:~$ sudo mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb2 on /media/Untitled 2 type hfsplus (rw,nosuid,nodev,uhelper=udisks)

```

---

### Post by vegetopia on 2010-12-18
does any of that mean anything to anyone?

---

### Post by vegetopia on 2010-12-18
Well, I fixed it! I prepared a USB drive with SLAX and booted from it. Then ran *fsck /dev/sda1* from a slax terminal and it fixed the file system. I was able to boot the computer and retrieve my data! Thanks to everyone for their help.

---

### Post by pellgarlic on 2010-12-21
ah, cool - glad you got it sorted =) (sorry - didnt have time to check back over the weekend...)

---

### Post by vegetopia on 2010-12-21
:wink:

---

