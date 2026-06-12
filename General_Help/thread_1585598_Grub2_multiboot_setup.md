---
title: "Grub2 multiboot setup"
date: 2010-09-30
forum: General Help
---

### Post by And6ate9 on 2010-09-30
I previously had a multiboot setup with grub in its own boot partition. The setup worked nicely and was easy to maintain. However, after install a current version of Ubuntu Grub2 has taken over my mbr, and I can't seem to get grub back. 

I would like to know if I can setup grub2 like grub with it's own boot partition?

---

### Post by Herman on 2010-09-30
:) Yes, you can, but with the improvements that GRUB2 brings, there's hardly any reason for wanting to do that.

If you want to know how though, here it is,
When GRUB 2 is in its own dedicated partition it is 'operating system independent', so we can add or remove one or two operating systems without the inconvenience of losing the boot of the remaining operating systems.
Those of us who are multi-booting with more that two operating systems in their computer like to be able to set their own user friendly names for their operating systems. 
It's okay to edit the grub.cfg directly when GRUB 2 isn't part of an operating system, making it easier to do what we like with GRUB and have fun with it and learn more GRUB commands and tricks.

[LIST=1]
[*]Choose an existing partition or create a new one and format it with a file system, you will need at least about 60 MiB of space in the partition for grub 2 files, but a little more room than that might be advisable.
[*]Format the partition with a file system and optionally give the file system a LABEL using GParted or a command appropriate for your choice of file system.
[*]Mount the partition - Usually to do that you just have to click on the icon in the 'Places' menu.
[*]Run a grub-install command similar to the one shown below,
[/LIST]
```
sudo grub-install --root-directory=/media/grub2 /dev/sda
```Where: '/media/grub2' is the mount point for the file system I want to have GRUB files created in
Where:  I want to make a new /boot/grub directory and fill it with GRUB files.
Where: '/dev/sda' is the hard disk in which I want to write the stage1 code to MBR.

That command creates a new /boot and /boot/grub/ directory if one doesn't already exist, and creates or refreshes GRUB files in /boot/grub, all except for grub.cfg.
If you don't make a grub.cfg then  there will be no GRUB Menu and your computer will boot to a GRUB Command Line Interface.

If you want a GRUB Menu you need to make a grub.cfg file in /boot/grub.

The automatic way to make a standard grub.cfg would be to use the grub-mkconfig command, and alter the file path to make it point to the 'Dedicated'  /boot/grub/'.

You can make your own grub.cfg file manually and customize it in any way you like.
If you need an example to help you get started, look here,  [grub.cfg]("http://grub.enbug.org/grub.cfg") - Grub Wiki.
Later, you can also make and add other files such as background images. That is a more difficult and old fashioned way of doing things.

And that's how to do it.
I think that the need for a 'Dedicated GRUB Partition' may be a little dated now though, since GRUB2 is so easily able to scan a computer with OS-Prober and can add other operating systems to the GRUB Menu automatically when we run 'update-grub'.
It's easier to have a real Ubuntu installation (not a 'persistent' install), booting with GRUB2 in a USB flash memopry drive and each time you change operating systems in the computer, run 'sudo grub-mkconfig' in the flash memory Ubuntu and reboot. Then you'll have a new GRUB Menu in the flash memory Ubuntu listing all of the operating systems inside the computer and you can boot any one of them and then do what you want, install some other boot loader to MBR or whatever. 
Most people complain about GRUB2 at first, but once you get used to it and have ideas about how to make it do everything automatically for you that we used to have to do manually, you'll start to like it and be spoiled, and you won't want to go back to GRUB Legacy and manual editing anymore. :)

---

### Post by And6ate9 on 2010-10-09
OK, I see that grub2 can do things automatically, and I guess it's just easier to let grub2 do its thing.  But how do I remove it from the mbr in case I just want my computer to boot straight into windows?  I have been scratching my head trying to figure that out.  Also, I thought it was bad to have grub in the mbr?

---

### Post by Herman on 2010-10-09
There's no need to remove GRUB from the MBR to boot Windows.
You can change the entry that's booted by default by opening your /etc/default/grub file with the test editor gedit, (or any test editor), and replace the 0 (zero) after the words 'GRUB_DEFAULT=' with the word 'saved', and run sudo update-grub or sudo grub-mkconfig -o /boot/grub/grub.cfg (whichever you prefer), then run 'sudo grub-set-default'. 
```
gksudo gedit /etc/default/grub
```
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=[COLOR=Sienna]**saved**[/COLOR]
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="elevator=deadline"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x1200

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"
```
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
```
sudo grub-set-default[COLOR=Red]** X**[/COLOR]
```
Where: '[COLOR=Red]**X**[/COLOR] ' is the line number counting down from the top of the GRUB Menu if the Ubuntu entry at the top is number 0 (zero).

After it's set up the first time it's easier after that, all you need to do is run 'grub-set-default' to change the default boot entry, as long as you leave the other settings be. :) 

> Also, I thought it was bad to have grub in the mbr? 	:confused: Why?

---

### Post by vikrang on 2010-10-27
Maybe some of us are still in the comfort zone of Windows and want to be safe than sorry! I have had the experience of screwing up the Win boot "n" no of times and running all sorts of utilities to fix /restore due to the fear of my wife and Parents flipping their lid when they dont see the 4 coloured box on switching the power!!
 
GRUB2 is fantastic.. But I think what Andgate means is to restore Windows to its virgin state ...You are talking abt setting Windows to default after the timeout...But  I think he is referrring to a case (which I have encountered a lot of times!) wherein he just wants windows to take over sans Grub...( no multiboot)...In that case , I think only way to do is with the help of WIn Installation disc or a utility (EasyBCD /Mbrfix) 
 
I have long wanted a boot manager which centrally controls everything without any impact in MBR/ Boot sector...I tried utilities like Plop Boot Manager etc but finally resorted to GRUB.The only risk I feel is without a linux system , GRUB may create a problem (ie , suppose I uninstall all Linux and want only Win)

---

### Post by rijnsma on 2010-11-14
It's an awfull business with that Grub2. I know... :confused: :)
Before you do anything: because there could be a problem, and there will be for some people when multibooting 
with this Grub2...:
[http://forums.pcpitstop.com/index.php?/topic/190076-grub-error-no-such-device/](http://forums.pcpitstop.com/index.php?/topic/190076-grub-error-no-such-device/)
but first:
make it possible to boot from a made-before hybrid _CD_ your system (kind of bootloader) and so go in your OS 
when nothing does work right anymore:
[http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)
Just in case...

Then you can patiently an diligently work in that booted OS. For instance you could be making a bootfile like menu.lst 
(but then the new kind) that fits (and which maybe boots all your distro's and Windows's on several partitions). 
It is unbelievable that this Grub2 is used while there is no program which does all the (BIG) hustle. 

And by the way: if you like to understand what they have produced for Linux etc. to boot: some tutorial and docs: 

Grub2:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId703454](http://www.dedoimedo.com/computers/grub-2.html#mozTocId703454)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1585598](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1585598)
Ex.:
[http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg)

There is much, much more info to make strange things simple.
Because this is not. Say it is confusing and it is unnecessary painful for a user.

(M$ has said it is time for Linux to say 'goodbye' to the world.
I hope they were wrong, but this indeed does help.)

---

### Post by sefs on 2010-12-07
> **Herman said:**
> :) Yes, you can, but with the improvements that GRUB2 brings, there's hardly any reason for wanting to do that.

If you want to know how though, here it is,
When GRUB 2 is in its own dedicated partition it is 'operating system independent', so we can add or remove one or two operating systems without the inconvenience of losing the boot of the remaining operating systems.
Those of us who are multi-booting with more that two operating systems in their computer like to be able to set their own user friendly names for their operating systems. 
It's okay to edit the grub.cfg directly when GRUB 2 isn't part of an operating system, making it easier to do what we like with GRUB and have fun with it and learn more GRUB commands and tricks.

[LIST=1]
[*]Choose an existing partition or create a new one and format it with a file system, you will need at least about 60 MiB of space in the partition for grub 2 files, but a little more room than that might be advisable.
[*]Format the partition with a file system and optionally give the file system a LABEL using GParted or a command appropriate for your choice of file system.
[*]Mount the partition - Usually to do that you just have to click on the icon in the 'Places' menu.
[*]Run a grub-install command similar to the one shown below,
[/LIST]
```
sudo grub-install --root-directory=/media/grub2 /dev/sda
```Where: '/media/grub2' is the mount point for the file system I want to have GRUB files created in
Where:  I want to make a new /boot/grub directory and fill it with GRUB files.
Where: '/dev/sda' is the hard disk in which I want to write the stage1 code to MBR.

That command creates a new /boot and /boot/grub/ directory if one doesn't already exist, and creates or refreshes GRUB files in /boot/grub, all except for grub.cfg.
If you don't make a grub.cfg then  there will be no GRUB Menu and your computer will boot to a GRUB Command Line Interface.

If you want a GRUB Menu you need to make a grub.cfg file in /boot/grub.

The automatic way to make a standard grub.cfg would be to use the grub-mkconfig command, and alter the file path to make it point to the 'Dedicated'  /boot/grub/'.

You can make your own grub.cfg file manually and customize it in any way you like.
If you need an example to help you get started, look here,  [grub.cfg]("http://grub.enbug.org/grub.cfg") - Grub Wiki.
Later, you can also make and add other files such as background images. That is a more difficult and old fashioned way of doing things.

And that's how to do it.
I think that the need for a 'Dedicated GRUB Partition' may be a little dated now though, since GRUB2 is so easily able to scan a computer with OS-Prober and can add other operating systems to the GRUB Menu automatically when we run 'update-grub'.
It's easier to have a real Ubuntu installation (not a 'persistent' install), booting with GRUB2 in a USB flash memopry drive and each time you change operating systems in the computer, run 'sudo grub-mkconfig' in the flash memory Ubuntu and reboot. Then you'll have a new GRUB Menu in the flash memory Ubuntu listing all of the operating systems inside the computer and you can boot any one of them and then do what you want, install some other boot loader to MBR or whatever. 
Most people complain about GRUB2 at first, but once you get used to it and have ideas about how to make it do everything automatically for you that we used to have to do manually, you'll start to like it and be spoiled, and you won't want to go back to GRUB Legacy and manual editing anymore. :)

I am looking to do this exact same thing either by dedicated partition or preferably by the automatic way with grub-scan.  But your explanation is lost upon me.

I want to boot a number of OS (none of them windows) from one box.  Some will be installed, some would have been put there from a backed up image made from ghost/dd/whatever.

I want to whenever i choose do something to grub2 which would rescan the disc and pick up any changes in the oses i have on the box, and what you describe above sounds exactly like I want it...only thing i want this to be done on the box, i don't want have to boot the box with the usb key all the time, but from the actual hdd in the box.  Is that possible or do i need to boot from a separate usb key.

My original thread is here .. [http://ubuntuforums.org/showthread.php?p=10212562](http://ubuntuforums.org/showthread.php?p=10212562)

Thanks.

---

### Post by Herman on 2010-12-07
;) All you need to do is keep Ubuntu as the main operating system inside the computer, and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg'  after adding or removing operating systems to or from your computer. 
If you are going to put them there from a backed up image made from ghost/dd/whatever that's all you'll need to do.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```That command will cause Ubuntu's GRUB to scan your computer and all attached disks and add them to the GRUB Boot Menu automatically.
If you get tired of typing the same command you could even paste it into a script and add a button to run in in one of your menus.

If you are installing other operating systems (from CD perhaps), and they write their boot loaders to MBR, (as most operating systems do when we install), you may need to re-install Ubuntu's GRUB to MBR again. 
If you can easily boot Ubuntu from the other operating system's boot loader and do that it's no problem, just boot and re-install GRUB.
If you install an operating system that doesn't support Ubuntu (maybe because not all other GNU/Linux distros use the ext4 file system yet), then you will need to either use the Ubuntu-in-a-USB trick, or Super Grub Disk or find some other way to boot Ubuntu in order to return your computer to normal again. You only have to boot Ubuntu once to re-install GRUB to MBR, or you can chroot and do it. There are many ways to do things, but some are easier and others require more learning.

A 'Dedicated GRUB Partition' is not needed anymore, but some people still think it's fun to have one. I don't have one anymore myself, but it's up to you if you are the owner of the computer.  :)

---

### Post by sefs on 2010-12-08
> **Herman said:**
>  it's no problem, just boot and re-install GRUB.
If you install an operating system that doesn't support Ubuntu (maybe because not all other GNU/Linux distros use the ext4 file system yet), then you will need to either use the Ubuntu-in-a-USB trick, or Super Grub Disk or find some other way to boot Ubuntu in order to return your computer to normal again. You only have to boot Ubuntu once to re-install GRUB to MBR, or you can chroot and do it.

From what you say above then I should always be able to boot from a live cd or a live usb to do the above.  Is that is so, it would be perfect.

> **Herman said:**
> 
All you need to do is keep Ubuntu as the main operating system inside the computer, and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' after adding or removing operating systems to or from your computer.
 

Ubuntu would not be on the machine at all but I would always have access to a live usb/cd with ubuntu on it.  SO I should be able to reinstall grub or run the above command when ever I need from the the live usb/cd?

I think the workflow will be something like this.

If i install an os from a backup image run grub-mkconfig from the live cd/usb disk.

If i install an os from it's install disk, re-install grub from live cd/usb disk. I am assuming in the install of grub it auto runs the grub-mkconfig, otherwise I would install and then run that to do the scan.

If I can do that then that would be all I need.

I cannot wait to give this a spin.

---

### Post by Herman on 2010-12-08
>   SO I should be able to reinstall grub or run the above command when ever I need from the the live usb/cd?No, I don't think you understand yet.

If you* install *Ubuntu in a USB flash memory stick then it will boot with  GRUB2. Then you can use it to run 'sudo grub-mkconfig -o  /boot/grub/grub.cfg' to scan your computer and add all operating systems  to the GRUB Menu and reboot the USB flash memory stick Ubuntu installation again. You should be able to boot any operating  system from your USB Ubuntu's GRUB Menu.

If you just  use a Live CD or make a USB from a Ubuntu CD you can use it to [chroot into a Ubuntu operating system to re-install GRUB with]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#chroot"). OR you can use it to [re-install GRUB in a Ubuntu installation from a Live CD without the need to chroot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD").

However it will do you no good to run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' from a Live CD to add strange operating systems to the boot menu for two reasons. 
One is because a Live CD won't remember the changes when you reboot  and boot off the new GRUB Menu, (if there was one). 
Secondly, even a Live CD or a 'Persistence' type of USB installation, (which works like  a Live CD and boots with syslinux and contains the Ubuntu installer),  sudo grub-mkconfig -o /boot/grub/grub.cfg won't work because Ubuntu Live CD boots with syslinux, not GRUB.

SO, you need [Super Grub Disk]("http://www.supergrubdisk.org/") for that instead. Then you can boot right from the CD or USB. 
A better idea might be to try a [Parted Magic Live CD]("http://partedmagic.com/") or USB, which includes Super Grub Disk plus a lot of other useful programs that you will find useful. :)

---

### Post by sefs on 2010-12-08
> **Herman said:**
> No, I don't think you understand yet.

If you* install *Ubuntu in a USB flash memory stick then it will boot with  GRUB2. Then you can use it to run 'sudo grub-mkconfig -o  /boot/grub/grub.cfg' to scan your computer and add all operating systems  to the GRUB Menu and reboot the USB flash memory stick Ubuntu installation again. You should be able to boot any operating  system from your USB Ubuntu's GRUB Menu.

If you just  use a Live CD or make a USB from a Ubuntu CD you can use it to [chroot into a Ubuntu operating system to re-install GRUB with]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#chroot"). OR you can use it to [re-install GRUB in a Ubuntu installation from a Live CD without the need to chroot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD").

However it will do you no good to run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' from a Live CD to add strange operating systems to the boot menu for two reasons. 
One is because a Live CD won't remember the changes when you reboot  and boot off the new GRUB Menu, (if there was one). 
Secondly, even a Live CD or a 'Persistence' type of USB installation, (which works like  a Live CD and boots with syslinux and contains the Ubuntu installer),  sudo grub-mkconfig -o /boot/grub/grub.cfg won't work because Ubuntu Live CD boots with syslinux, not GRUB.

SO, you need [Super Grub Disk]("http://www.supergrubdisk.org/") for that instead. Then you can boot right from the CD or USB. 
A better idea might be to try a [Parted Magic Live CD]("http://partedmagic.com/") or USB, which includes Super Grub Disk plus a lot of other useful programs that you will find useful. :)

I think I understand a little better.  I may indeed need the dedicated boot partition after all, as I want to have what ever the flash is doing directly on the system. That is I want to power on and have grub come up from the system itself and not any inserted media.

---

### Post by Herman on 2010-12-08
> I think I understand a little better.  I may indeed need the dedicated  boot partition after all, as I want to have what ever the flash is doing  directly on the system. That is I want to power on and have grub come  up from the system itself and not any inserted media. 	:D Okay, you can do that, but be aware that as you are proposing to install just GRUB2 independent of any operating system it won't be under the control of any operating system either.
When GRUB2 is part of Ubuntu it is updated by scripts and programs that are part of the operating system, so you will need to manually edit your grub.cfg file the same as we used to need to do when we used Legacy GRUB.
You can still use the 'sudo grub-mkconfig command with the -o option to throw your grub.cfg in whatever file path you want such as in /media/<file system UUID>/boot/grub/grub.cfg from a Ubuntu installation that has GRUB2 in it. You would still need Ubuntu installed either in a hard disk or USB flash memory stick for that I think, (unless someone proves me wrong, I tried from a Live CD installed in a USB this morning and was given an error message but ran out of time for further testing.)
It is quite simple to use a Live CD operating system to manually edit your grub.cfg though, as long as you know what you are doing.
Do whatever you like as long as you're having fun. :)

---

### Post by sefs on 2010-12-08
Thanks for the help! I will play around with it to see what comes up.

---

### Post by sefs on 2010-12-09
Hi I have some follow up questions...

I need to figure out the cfg  it lookes mighty complex, but the sample given here... was very simple.  Can I indeed have a cfg file this simple?

```

# Timeout for menu
set timeout=10

# Set default boot entry as Entry 0
set default=0

# Entry 0 - Load Linux kernel
menuentry "My Linux Kernel on (hdx,x)" {
    set root=(hdx,x)
    linux /vmlinuz root=/dev/hda1
    initrd /initrd
}

# Entry 1 - Chainload another bootloader
menuentry "Ubuntu Lucid 10.04" {
	recordfail
	insmod ext2
	set root='(hdx,x)'
	search --no-floppy --fs-uuid --set 0ea291b3-1127-4232-ae39-397ce9ad4be4
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=0ea291b3-1127-4232-ae39-397ce9ad4be4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}

menuentry "Microsoft Windows 7" {
        insmod ntfs
        set root='(hdx,x)'
        search --no-floppy --fs-uuid --set 72e245e4e245ace3
        chainloader +1
}

```

Some questions...
1) How would I determine hdx,x?
2) How do I determine those long numbers after fs-uuid?
3) Is Entry 0 suppose to be my dedicated grub2 entry? When I created the partitions for the system the grub2 dedicated is the only one I flaged as boot in gparted.

Thanks.

---

### Post by Herman on 2010-12-09
> Can I indeed have a cfg file this simple?Probably. GRUB will just run the commands in the order they appear in the file.

incidentally, your "# Entry 1 - Chainload another bootloader" comment seems to be a little misleading, the stanza under it appears to be a series of commands for a direct kernel boot.
In that case it would be better to use a symlink boot instead, like,
```
# Entry 1 - boot Ubuntu by symlinks
menuentry "Ubuntu Lucid 10.04" {
    recordfail
    insmod ext2
    set root='(hdx,x)'
    search --no-floppy --fs-uuid --set 0ea291b3-1127-4232-ae39-397ce9ad4be4
    linux    /vmlinuz root=UUID=0ea291b3-1127-4232-ae39-397ce9ad4be4 ro   quiet splash
    initrd    /initrd.img
```Booting by symlinks means you won't need to update the boot.cfg every time you receive a kernel update.

---

### Post by Herman on 2010-12-09
It would be a good idea to include a recovery entry, just in case,
```
menuentry 'Ubuntu, Lucid 10.04 (recovery mode)' {
    recordfail
    insmod ext2
    set root='(hdx,y)'
    search --no-floppy --fs-uuid --set 0ea291b3-1127-4232-ae39-397ce9ad4be4
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /vmlinuz root=UUID=0ea291b3-1127-4232-ae39-397ce9ad4be4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img
}
```

---

### Post by Herman on 2010-12-09
> 1) How would I determine hdx,x?
2) How do I determine those long numbers after fs-uuid?
Run 'sudo blkid'
```
sudo blkid
```

---

### Post by Herman on 2010-12-09
> 3) Is Entry 0 suppose to be my dedicated grub2 entry? When I created the  partitions for the system the grub2 dedicated is the only one I flaged  as boot in gparted.Your entry 0 should boot any GNU/Linux operating system in your first hard disk via the symlinks after you edit it with appropriate numbers to replace x's in the '(hdx,x)'s with numbers.
The 'root=/dev/hda1' part specifies the partition 1 of your first hard disk as the partition which contains the /sbin/init and therefore determines the / (root) file system.
Actually, we use '/dev/sda1' now instead of '/dev/hda1', I'm not sure how vital it is, but you should try replacing the 'h' with an 's' there, especailly if you have any trouble.

The boot flag is completely irrelevant to GRUB and GNU/Linux operating systems as far as I know. :)

---

### Post by sefs on 2010-12-09
> **Herman said:**
> Your entry 0 should boot any GNU/Linux operating system in your first hard disk via the symlinks after you edit it with appropriate numbers to replace x's in the '(hdx,x)'s with numbers.
The 'root=/dev/hda1' part specifies the partition 1 of your first hard disk as the partition which contains the /sbin/init and therefore determines the / (root) file system.
Actually, we use '/dev/sda1' now instead of '/dev/hda1', I'm not sure how vital it is, but you should try replacing the 'h' with an 's' there, especailly if you have any trouble.

The boot flag is completely irrelevant to GRUB and GNU/Linux operating systems as far as I know. :)

What I was trying to find out with this question is how does the system know to go to the dedicated partition holding grub2 in its start up process, is there something special I was to do?

---

### Post by sefs on 2010-12-09
We have lift off.... :)

What I need to do now is the symlink thing, and its 99% as I want it.

---

### Post by Herman on 2010-12-09
> **sefs said:**
> What I was trying to find out with this question is how does the system know to go to the dedicated partition holding grub2 in its start up process, is there something special I was to do?When you install GRUB to MBR, you issue a command something like: sudo grub-install --root-directory=/media/grub2 /dev/sda'. The --root-directory part of the command specifies the directory to make a /boot/grub directory in to be filled with GRUB files, and the /dev/sda part of the command specifies where you want to put the boot.img and core.img.
The boot.img in the MBR starts the core.img in the first track of the hard disk and the core.img is custom made by assembling files like diskboot.img, kernel.img, pc.mod and ext2.mod and those files know which file system they belong to and look for other GRUB files there such as  normal.mod and other modules.

So if you have more than one 'Dedicated GRUB Partition', whichever GRUB partition you have installed to MBR will be the one that will be loaded automatically.

If you are interested, you could try a series of experiments. Try making several different 'Dedicated GRUB Partitions' and run the grub-install command to install a different GRUB to MBR and boot to see if I'm correct or prove me wrong. You could have GRUB Menus with different colors or different background images so you can tell which is which. :D

---

### Post by Herman on 2010-12-09
> What I need to do now is the symlink thing, and its 99% as I want it.Symlinks are found in /, (at the top of the file system heirarcy or tree),
> herman@amd-quad-lynx:~$ ls /
bin   cdrom  etc   [COLOR=Red]**initrd.img**[/COLOR]      lib    lib64       media  opt   root  selinux  swapfile  tmp  var      vmlinuz.old
boot  dev    home  initrd.img.old  lib32  lost+found  mnt    proc  sbin  srv      sys       usr  [COLOR=Red]**vmlinuz **[/COLOR] xorg.conf.new
These symlinks point to whichever is the latest kernel and initrd.img file is most current in /boot/grub, (or at least they normally do, unless some weird error has occurred).
So instead of using the file path specifically addressing your latest /boot/vmlinuz followed by its number, you just boot it by the symlink, ditto with /boot/initrd.img.
The term 'symlink' is probably a strange term for some people, if you are from Windows you might understand better if I used the word 'shortcut' instead.

---

### Post by sefs on 2010-12-09
> **Herman said:**
> Symlinks are found in /, (at the top of the file system heirarcy or tree),
These symlinks point to whichever is the latest kernel and initrd.img file is most current in /boot/grub, (or at least they normally do, unless some weird error has occurred).
So instead of using the file path specifically addressing your latest /boot/vmlinuz followed by its number, you just boot it by the symlink, ditto with /boot/initrd.img.
The term 'symlink' is probably a strange term for some people, if you are from Windows you might understand better if I used the word 'shortcut' instead.

I see. That's even more elegant.  Now I won't have to do anything at all almost.  I was going into the boot dir and manually symlinking to a file that I then called in the grub.cfg.  But that way is much nicer. I would have had to create new symlinks with every kernel update.

Thank you.

---

### Post by sefs on 2010-12-09
> **Herman said:**
> When you install GRUB to MBR, you issue a command something like: sudo grub-install --root-directory=/media/grub2 /dev/sda'. The --root-directory part of the command specifies the directory to make a /boot/grub directory in to be filled with GRUB files, and the /dev/sda part of the command specifies where you want to put the boot.img and core.img.
The boot.img in the MBR starts the core.img in the first track of the hard disk and the core.img is custom made by assembling files like diskboot.img, kernel.img, pc.mod and ext2.mod and those files know which file system they belong to and look for other GRUB files there such as  normal.mod and other modules.

So if you have more than one 'Dedicated GRUB Partition', whichever GRUB partition you have installed to MBR will be the one that will be loaded automatically.

If you are interested, you could try a series of experiments. Try making several different 'Dedicated GRUB Partitions' and run the grub-install command to install a different GRUB to MBR and boot to see if I'm correct or prove me wrong. You could have GRUB Menus with different colors or different background images so you can tell which is which. :D

Ah boy, I will test this one out over the weekend.

---

### Post by And6ate9 on 2011-02-18
Nice this thread comes up first when searching multiboot.
Any way. I have ahad a busy couple of months, and now I am ready to get started on this again.

So Hermen, the a good way do go is to install ubuntu to usb? and that will update all my distro and act as a sort of safety booter at the same time? Interesting.

I don't mind editing grub2 if it's in it's own partition. I did that for grub legacy and it was not bad. In fact I chain booted from the independant grub to each distro grub. That way I didn't do much editing when the distros updated their kernel.
Is the same possible with grub2

before I was booting from grub legacy into grub2. That worked just fine till I over wrote the mbr with grub2 during a new install. I can't seem to get grub legacy back into the mbr.
That's why I thought I might as well just upgrade to grub2.

---

### Post by Herman on 2011-02-19
:D If you install Ubuntu in a USB external flash memory drive, it can be quite useful as an auxilliary operating system for times when you want to travel light and still have your own Ubuntu operating system with you.
It can also be handy to have on the rare occasions when your computer's internal Ubuntu operating system has some kind of a problem and maybe can't boot. 
That might happen when setting up a multi-boot with other operating systems, especially if you install some other operating system after Ubuntu and it installs its own boot loader to MBR.

You can use a utility and rescue CD such as Super Grub Disk or Parted Magic, (which also contains Super Grub Disk now and Super Grub2 Disk as well).  I have always liked Super Grub Diisk and Parted Magic, and I still like to have an up to date version of that distro on hand, and I use it quite often.

There are a couple of extra things we can do when we have a Ubuntu operating system working on another Ubuntu that we might not be able to do with another distro, or at least not as well. 
If you boot Ubuntu installed in a USB (as a regular installation so that it boots with GRUB2, not as a 'Persistence' (Live CD type of installation), which boots with syslinux), it's easy to run grub-mkconfig and update the USB Ubuntu's GRUB2. After that we can reboot the USB and stop at the USB's GRUB Menu and pick any operating system from the list and boot it.
If the operating system in question still cannot boot, then you have the opportunity to boot Ubuntu in the USB again instead, where you can run tests to try to diagnose the problem and you have the tools you need to fix it in most cases.
Sometimes, there might be a problem with an incomplete update of software in the broken operating system, and in that case we really need another Ubuntu system to work from. We can 'chroot' into the internal operating system and run apt-get update and apt-get upgrade and fix our broken system. 

GRUB2 is different from GRUB Legacy in the way it is designed to be more integrated with the operating system and has the ability to scan the computer, detect other operating systems, and update its boot menu automatically. I think that's a wonderful thing. We can make use of that amazing and important feature. 

Regards, Herman :)

---

### Post by And6ate9 on 2011-02-19
Ok super grub disk and partmagic, check.

What's your method of installing to the usb?

For some reason the live ubuntu disks don't load for me since 8.04.
it would be nice to book from usb.

I have to get my linux back up and running.

---

### Post by Herman on 2011-02-20
[This]("http://members.iinet.net.au/%7Eherman546/p24.html") web page or [this]("http://members.iinet.net/%7Eherman546/p19.html") one explain how to install Ubuntu in any removable or non-first drive.

If you don't have a working CD or DVD drive, I'm not sure what to tell you. You either need to fix your optical drive or buy a new one if you can afford it. 
I you're handy with a screwdriver, I have a page on how to [clean your optical drive lens]("http://members.iinet.net.au/%7Eherman546/p27.html").

I was going to tell you might be able to make a Ubuntu Startup Disk by taking your Ubuntu Live CD and an empty USB flash memory stick to a friend's computer and using that to boot the Live CD and run 'System',->'Administration'->'Startup Disk Creator'. That will make you a USB which behaves like a Live CD, it boots with syslinux and contains the Ubuntu Installer. That's the way I do it if a computer doesn't have an optical drive. 
I'm a little reluctant to tell you that though, Startup Disk Creator is a little bit risky and if you're not used to it you might accidentally overwrite your friend's internal drive and operating system and all his or her files by accident, and I don't want to tell you to do that. If you have a friend who doesn't mind removing the hard disk(s) from their computer it might be okay. Some people are quite comfortable with working with their computers internal parts and others are not.

For another idea, I have heard of something called 'unetbootin', by which I think you can install Ubuntu from the internet somehow, but I haven't tried it so I cannot give you any advice on that. Someone else can probably advise you on unetbootin.

Regards, Herman :)

---

### Post by YesWeCan on 2011-02-20
Dual booting with Windows is still such a prolific issue.

What I would like to know is why a sort of Trojan Horse thing hasn't been invented to disguise a Ubuntu installation so it looks like another Windows OS to the Windows bootloader? Could this not be achieved with the right stuff in the Ubuntu partition boot record and maybe a few other bits of obfuscation? Then there would be no need to mess with your Windows MBR and you'd use Windows bootloader menu to select Ununtu.
Just a thought.


Also, this manual update-grub/mkconfig etc is all a real faff. Why doesn't Grub always do a scan for OSes whenever it runs and then when you choose an OS it goes and gets whatever it needs to boots it. Is its unfortunate dependency on Ubuntu (for example) because it is sardined into a "mostly unused" 63 sectors of disk space (a sort of hack in itself) and doesn't have enough code to generate the necessary boot files dynamically? Is that why?

If so, why isn't Grub's core.img located in the sectors immediately following the PBR of the Ubuntu partition and before the OS? Or even in its own, small partition? Give it 1MB of space before the OS so it can do its thing dynamically and automatically.

---

### Post by oldfred on 2011-02-20
i have three bootable USB drives, all using grub2. Ok, I like grub2 and somewhat like if you only have a hammer, everything looks like a nail. I boot everything with grub2.

I followed Herman's instructions for a full install to my USB. It is basically just another install to a second drive.

To install to the USB, I stopped using CDs and converted to USB. But I used grub2 and loopmounted the ISO file. I find it easier just to copy ISO and make minor edits to grub.cfg on flash drive. Since this flashis 4GB I also copy in gparted, several versions of Ubuntu, and other repair type ISOs loop mounted. Handy for both installs & repairs.

After I manually created it, I found this:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

I also have a windows repairCd that I now boot with grub2, so I can use more than the small amount of space that the windows repair install takes.

---

### Post by Herman on 2011-02-20
:) Yeah, I agree that dual booting is a less than optimal situation.
Personally I would prefer if all new computers came with Ubuntu pre-installed in them and if a person wants a proprietary operating system for some reason they would need to purchase it separately and install it themselves or have a technician do it for them. 

I assemble my own computers now and install Ubuntu only in then and they work great and I save a lot of money too, so I can afford better hardware. The last store-bought computer I purchased had Ubuntu pre-installed in it. I don't think there is any real reason anyone should need to dual boot with Windows really, free and open source is the way to a better future. :)

---

### Post by And6ate9 on 2011-02-21
Its not that the drive is not working it's that the live cd at least Ubuntu live cd is not booting my computer since 8.04. 8.04 still boots fine. So, I have been install Ubuntu with the alternative cd. I am hoping that a usb live version may work better.

> **Herman said:**
> [This]("http://members.iinet.net.au/%7Eherman546/p24.html") web page or [this]("http://members.iinet.net/%7Eherman546/p19.html") one explain how to install Ubuntu in any removable or non-first drive.

If you don't have a working CD or DVD drive, I'm not sure what to tell you. You either need to fix your optical drive or buy a new one if you can afford it. 
I you're handy with a screwdriver, I have a page on how to [clean your optical drive lens]("http://members.iinet.net.au/%7Eherman546/p27.html").

I was going to tell you might be able to make a Ubuntu Startup Disk by taking your Ubuntu Live CD and an empty USB flash memory stick to a friend's computer and using that to boot the Live CD and run 'System',->'Administration'->'Startup Disk Creator'. That will make you a USB which behaves like a Live CD, it boots with syslinux and contains the Ubuntu Installer. That's the way I do it if a computer doesn't have an optical drive. 
I'm a little reluctant to tell you that though, Startup Disk Creator is a little bit risky and if you're not used to it you might accidentally overwrite your friend's internal drive and operating system and all his or her files by accident, and I don't want to tell you to do that. If you have a friend who doesn't mind removing the hard disk(s) from their computer it might be okay. Some people are quite comfortable with working with their computers internal parts and others are not.

For another idea, I have heard of something called 'unetbootin', by which I think you can install Ubuntu from the internet somehow, but I haven't tried it so I cannot give you any advice on that. Someone else can probably advise you on unetbootin.

Regards, Herman :)

---

### Post by kuifje09 on 2011-02-24
Reading a lot of the multiboot, I still don't understand how windows 98 would fit in one of the menus.
It is definitly not picked up automaticly.
Where does this lines stand for in 30_os-prober
      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*)
Do I have to change those line here? or should I create a new menu or would it fit in 40_custom

I could install old grub again, I can read and write with it, but one day it want work nomore I guess.
So it is better to learn a bit more again...

Did someone find a solution to make it posible to boot windows 98 again.
Does it has to do something with the name ?  or with the disknumber i.e  hd0.0

Okay, I possibly found the answer here:
[http://ubuntuforums.org/showthread.php?t=1630631](http://ubuntuforums.org/showthread.php?t=1630631)

---

### Post by Herman on 2011-02-24
:D Well I am absolutely positive that GRUB can pick up Windows 98 and add it to the boot menu automatically, or at least it worked a number of times for me when I made this installation example page,[COLOR=#000000] [/COLOR][COLOR=#000000][Ubuntu With Windows. ]("http://members.iinet.net.au/%7Eherman546/p2.html")At least it works for me. (Unless support for it has been dropped since Lucid Lynx 10.04, but I may have installed 10.10 in that computer since and not bothered updating the web page, not sure now since I borrowed the hard disk out of it for RAID experiments and wiped it).

Maybe try running a file system check (scandisk), and defragging Windows 98 a few times and try again.
Another idea might be to try refreshing your Windows 98 boot sector and boot loader files with your Windows 98 floppy disk and some of the commands illustrated in this link, [/COLOR][Windows 98]("http://members.iinet.net.au/%7Eherman546/p15.html#Windows_98") in case any of those are a little corrupted or fading.

I actually really like Windows 98, my Windows 98 SE is as fast as lightning when it has been well defragged and runs well even with only a small amount of ram and a modest CPU. It can do everything you really need. :D
            [COLOR=#000000] [/COLOR]

---

