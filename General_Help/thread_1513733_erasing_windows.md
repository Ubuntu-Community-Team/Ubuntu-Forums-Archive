---
title: "erasing windows"
date: 2010-06-19
forum: General Help
---

### Post by beelzebufo on 2010-06-19
I want to completely wipe windows off my laptop, but don't want to lose my ubuntu, how do I do that?

---

### Post by Primefalcon on 2010-06-19
Boot from a live disk, open gparted, delete the windows partition, resize the Ubuntu partition to take up all remaining space

---

### Post by elliotn on 2010-06-19
Make sure the ntfs partition is not mounted.

---

### Post by karthick87 on 2010-06-20
> **Primefalcon said:**
> Boot from a live disk, open gparted, delete the windows partition, resize the Ubuntu partition to take up all remaining space


How to resize the ubuntu partition to take up all the remaining space..?

---

### Post by beelzebufo on 2010-06-20
do I need to order a live disc or can I just use the one I burned?  I tried going to the boot menu and it just asks me which os I want to run.

---

### Post by Mark Phelps on 2010-06-20
If you burned a desktop CD, it IS a live disk already.

You neglected to mention whether or not you installed Ubuntu INSIDE Windows using Wibu.  I'm guessing you did not.  In which case, simply removing the Windows partition will leave Ubuntu intact.

If you can still boot to Ubuntu, just open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu, this time, without any MS Windows entries.  When you reboot, not only will they be gone, but since the new GRUB2 default is to boot directly into the OS when only one OS is present, you may not even see a menu.

---

### Post by beelzebufo on 2010-06-20
boy mark, I really want to call you names right now, but I know you didn't mean to screw anything up.  That completely destroyed ubuntu on my laptop, unrunnable.  So now I have uninstalled and am reinstalling using wibu.  thats what I must have done in the first place.

---

### Post by megamandos on 2010-06-20
Ok, so how this SHOULD have been done:

Boot to a live CD, open gparted, delete the windows partition

resize the ubuntu partition to take up the entire drive.

then mount the ubuntu partition (just look in the "Places" menu at the top of the screen and click on the ubuntu partition)

then open nautilus and navigate to /media and look for which folder is your ubuntu partition.

then open terminal and type in the following commands:

```

sudo -i
chroot /media/<your ubuntu's folder>
update-grub
shutdown -r now

```

your computer would have rebooted and shown the grub menu, and everything would have worked...

---

### Post by beelzebufo on 2010-06-20
I might should have put this thread in the absolute beginner talk... I still dont' get it.  I boot to a live disc and it just gives me the choose os screen, I choose ubuntu and there is no such thing as gparted soooooo, I dont get it, I know I am doing something wrong, but I think I am doing everything you guys are saying.  at the bios startup screen you hit f12 right? then choose boot from cd, then I get the choose xp or ubuntu screen so, I choose ubuntu... I am missing a step somewhere      aaarrrrgggghhhhh!!!!!

---

### Post by wilee-nilee on 2010-06-20
from Ubuntu run the script in my sig and post it in code tags. This will tell us exactly what and where everything is that we need to know to help you.

Also in the mean time you will need to know the key prompt to get to the choice of what to boot from,ie cd, hard drive floppy..etc without this information you wont be able to boot a live cd unless you go into the bios a rearrange the boot list, and this doesn't always insure that if the cd reader is first that it will boot a live cd.

You have not put enough information on the thread to really help you that is why I suggest the script.

---

### Post by megamandos on 2010-06-20
no no no, gparted is a program in the ubuntu live cd. Yeah you are missing a step, it seems that you aren't booting into the CD. Although I cant see how you are doing it wrong.

You choose boot from cd, then when you hear/see it reading from the disk, you should hit F2 repeatedly until a menu appears, it should have a purple-red-ish background, then select "Try ubuntu without installing it". then it should boot up into the "live cd". It will look like normal ubuntu. Then go to System>Administration>Gparted

Then gparted will scan your hard drive(s) for partitions, then display a partition map. you should see in there your ubuntu partition, and your windows partition. right click on your windows partition and click "delete", then right click on your ubuntu partition and click "Move/Resize" and then in the "free space preceding" and the "free space following" type "0". then click ok, then click the green checkbox at the top.

then:

then mount the ubuntu partition (just look in the "Places" menu at the  top of the screen and click on the ubuntu partition)

then open nautilus and navigate to /media and look for which folder is  your ubuntu partition.

then open terminal and type in the following commands:

```

sudo -i
chroot /media/<your ubuntu's folder>
update-grub
shutdown -r now 
```
your computer would have rebooted and shown the grub menu, and  everything would have worked...

---

### Post by beelzebufo on 2010-06-20
ok, i'm about to run that script, but what do you mean by code tags? sorry totally new to ubuntu, you pretty much have to be a programmer to use this thing it seems like.. oh well, I will get it... I don't know what other information you would need really

---

### Post by beelzebufo on 2010-06-20
oh, I see, let me try the f2 trick real quick

---

### Post by wilee-nilee on 2010-06-20
It can be frustrating in the beginning.;) if your in Ubuntu put the script on the desktop and run this command in the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh
``` 

Open the file that appears after running the code then copy and paste it to a reply and while the reply is still open highlight the whole text and click on the # in the reply panel.

This script has to be run from Linux. If you look in my sig you put the bracketed code at the beginning and /code at the end if the other method of highlighting doesn't work.

[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by beelzebufo on 2010-06-20
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       a35a91f2-e257-4199-aa45-d9da5542fe24   ext4                                     
/dev/sda1        EAD40A44D40A140B                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sr0         /media/Jun 15 2010       udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ead40a44d40a140b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ead40a44d40a140b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ead40a44d40a140b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

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

================= sda1/Wubi: Location of files loaded by Grub: =================


   5.1GB: boot/grub/grub.cfg
  15.1GB: boot/initrd.img-2.6.32-21-generic
  15.1GB: boot/vmlinuz-2.6.32-21-generic
  15.1GB: initrd.img
  15.1GB: vmlinuz

---

### Post by beelzebufo on 2010-06-20
wooops, hit post before hitting the number on the right side, sorry... and you totally rock for being patient with my dumb *** ... oh yeah, the f2 trick didn't work, hit f12, boot from cd, hit f2 over and over and still no gparted

---

### Post by wilee-nilee on 2010-06-20
Okay you have a wubi install so you can't just remove windows it will take Ubuntu with it. Mark Phelps was on the right track you just missed the wubi reference. No big deal we have all been there myself daily.;)

Do you want to save anything in Ubuntu? if you do back it up to a thumb or a external HD, or disc then we will get the Live cd to boot and install.

---

### Post by beelzebufo on 2010-06-20
no, when I did that update thing it totally killed my ubuntu so I reinstalled, so, nothing I want to save anymore.

---

### Post by wilee-nilee on 2010-06-20
> **beelzebufo said:**
> no, when I did that update thing it totally killed my ubuntu so I reinstalled, so, nothing I want to save anymore.

So the wubi is the fresh install, and you ran the script from it?

What is your computer model so we can narrow down the key prompt for bios and the boot from list. These will be different keys so the model will help to look on the web.

You wont need gparted if we can get the cd to boot we will just install to the whole hard drive.

---

### Post by beelzebufo on 2010-06-20
yes, I ran the script from the new install, ummm as far as a model goes, it is a dell latitude d620... and I can't remember the bios revision # but I could get it for you if you need it, i would just have to reboot... again

---

### Post by wilee-nilee on 2010-06-20
So as far as I can tell the f12 key should get you to a choice of booting devices, if this happens use the arrow key to start the boot with the cd drive, hit enter then start clicking the shift key repeatedly this should bring you to a screen that will let you choose the language and then try without installing. If this works when you get to the desktop hit install and let it install to the whole hard drive.

If you want to keep XP let us know that is not a problem.
If not just install.

So when you hit the power button to start the computer hit that f12 button immediately and repeatedly until you see it say looking for boot, or you see the screen to choose the boot from devices, HD, cd, floppy...etc

Hopefully it is f12 but it could be any f key or esc or any key really. If you know how to get to the bios you can also move the cd reader to the top of the list and this might work just fine to boot the cd

---

### Post by beelzebufo on 2010-06-20
aha, shift, I will try that

---

### Post by spiky001 on 2010-06-20
I think the OP is missing when to hit F key, When you see the dell logo right at begginig press F12 if it gose past logo with blue load line it,s gone to far

---

### Post by wilee-nilee on 2010-06-20
> **beelzebufo said:**
> aha, shift, I will try that

I saw the rootkit reference generally a full install should wipe that away. I doubt you really have one but you never know.

---

### Post by wilee-nilee on 2010-06-20
> **spiky001 said:**
> I think the OP is missing when to hit F key, When you see the dell logo right at begginig press F12 if it gose past logo with blue load line it,s gone to far

It takes a few times to get the hang of pounding that key immediately, then you recognize how to use it. I see the put cd 1st in bios all the time when the key prompt is the better method I think.

---

### Post by beelzebufo on 2010-06-20
no, I meant give me one, last time I got one it wiped out windows for me lol and no, I hit f12 at the right time, then I get to the boot from menu, I choose boot from cd, I tried f2, and now shift and it just takes me to the choose os screen, but I do get a prompt that gets me into a gnu command prompt, maybe that will do it, anyway thank you guys, I am done for the night, I like to think that I am a reasonably intelligent human being, but this makes me feel like a blithering retard.

---

### Post by wilee-nilee on 2010-06-20
Don't hit any f key after you choose the boot from cd, what distro are you trying to install. If it is karmic or Lucid the shift key will get you to the language choice and try without installing. Now if you just choose the boot and no other keys it will take a little time but you will get to a screen that offers install or run a live choice. The shift key prompt is to bypass this wait time only it is not necessarily needed to get to the live desktop.

If we get this going you will have learned some skills that will be a great help in the future.;)

---

### Post by beelzebufo on 2010-06-20
yeah, thanks, I really like ubuntu and look forward to learning all I can about it, I don't really think this is a ubuntu issue, I think that this is happening because I have dual booted xp and ubuntu.  you guys keep telling me to do the same thing though and i keep getting the choose os screen, no matter what.  I hit f12 at the dell bios screen, choose boot from cd, then I get the choose os screen, that's it, no matter what I do, if I hit f2, if I hit shift, if I hit nothing, same thing.  I have booted from cd with windows before too, so I have no idea why it won't let me do it with ubuntu and it's 10.04. my disk image is a .iso file, maybe that has something to do with it?

---

### Post by wilee-nilee on 2010-06-20
> **beelzebufo said:**
> yeah, thanks, I really like ubuntu and look forward to learning all I can about it, I don't really think this is a ubuntu issue, I think that this is happening because I have dual booted xp and ubuntu.  you guys keep telling me to do the same thing though and i keep getting the choose os screen, no matter what.  I hit f12 at the dell bios screen, choose boot from cd, then I get the choose os screen, that's it, no matter what I do, if I hit f2, if I hit shift, if I hit nothing, same thing.  I have booted from cd with windows before too, so I have no idea why it won't let me do it with ubuntu and it's 10.04. my disk image is a .iso file, maybe that has something to do with it?

You might have a bad cd burn the f2 key is to get into bios probably.

If you have a thumbdrive download unetbootin into windows and load the iso and boot it, from the boot choice from the f12 prompt. Or burn another cd at no faster then 4x and burn it as a image not a data file.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If your hitting both the f2 key and the shift key after choosing the boot then that may be a problem. I good cd if booted from the f12 prompt with no more keys clicked will get you to the desktop, via another screen to choose install or live desktop with lucid.

XP is not even being read when you boot from a live cd.

---

### Post by beelzebufo on 2010-06-20
it appears that my computer simply will not boot to the ubuntu iso is there another file extension that I can download or something? can I reconfigure my cd rom drive? or something?

---

### Post by Hman242 on 2010-06-20
You could always burn Gparted itself as a LiveCD if you have another computer available to do so.

---

### Post by Mark Phelps on 2010-06-21
> **beelzebufo said:**
> boy mark, I really want to call you names right now, but I know you didn't mean to screw anything up.  That completely destroyed ubuntu on my laptop, unrunnable.  ...

What part of my comment in my post (quoted below) did you NOT read:

> You neglected to mention whether or not you installed Ubuntu INSIDE Windows using Wubi. I'm guessing you did not. In which case, simply removing the Windows partition will leave Ubuntu intact.

IF it was a Wubi install, which after reading the other posts, it has become apparent it WAS, then of course, removing Windows will remove it.  That's how Wubi works!

---

### Post by beelzebufo on 2010-06-22
I owe you a bit of an apology mark, the language I used made it sound like I was blaming you, I know you were just trying to help and I got ahead of myself, that would have been very helpful advice had I known what I know now.  I am sorry if I offended you.  thank you for offering your advice, I am new to ubuntu and computers really, so I thought that wibu would just install ubuntu, I did not know that it installed it under windows.  I also burned the cd as a data cd not as an image, hopefully that will help. thanks again.  one more thing, will my install of ubuntu without windows still have the drivers to connect to the internet?  or have I been using the windows drivers under ubuntu?  keep in mind that the internet will not connect under windows.

---

### Post by wilee-nilee on 2010-06-22
> **beelzebufo said:**
> I owe you a bit of an apology mark, the language I used made it sound like I was blaming you, I know you were just trying to help and I got ahead of myself, that would have been very helpful advice had I known what I know now.  I am sorry if I offended you.  thank you for offering your advice, I am new to ubuntu and computers really, so I thought that wibu would just install ubuntu, I did not know that it installed it under windows.  I also burned the cd as a data cd not as an image, hopefully that will help. thanks again.  one more thing, will my install of ubuntu without windows still have the drivers to connect to the internet?  or have I been using the windows drivers under ubuntu?  keep in mind that the internet will not connect under windows.

The cd has to be a image burned. You are dead in the water if you can't boot from a USB or CD, the only other option would be a minimal install using a floppy.

Get somebody to help you with the booting from the cd if you can then we can help you.

---

### Post by beelzebufo on 2010-06-22
I have burned to a disc image, it is running off the boot menu right now, but it is taking forever, all I see is the ubuntu open screen with different colored dots.  going on 15 minutes is that normal?
and just to reiterate... thank all of you so much for being patient with my noobie ***, we will figure it out I got faith in the universe I deserve ubuntu!  I't would totally rock to have a single system boot with just ubuntu... at least I am learning as we go

---

### Post by wilee-nilee on 2010-06-22
> **beelzebufo said:**
> I have burned to a disc image, it is running off the boot menu right now, but it is taking forever, all I see is the ubuntu open screen with different colored dots.  going on 15 minutes is that normal?

That is unusual, at what speed did you burn the cd it should be the slowest possible 4x.

Also are you using the same ISO as before it might be a bad download.

If you do the key prompt to get the cd to boot then click on the shift immediately after choosing cd as before it will take you to a screen that has a test cd option. This shift key option will also take you to the same screen which gives you the option to try without installing, which is a quicker and more controllable option, due to the choices given on that screen.

Here is a link to burning the ISO.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I would suspect the original ISO download though and if you have no download limits do it from here, make sure it is 32 bit I suspect that is what you have.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Mark Phelps on 2010-06-22
> **beelzebufo said:**
> ... one more thing, will my install of ubuntu without windows still have the drivers to connect to the internet?  or have I been using the windows drivers under ubuntu?  keep in mind that the internet will not connect under windows.

When you run Ubuntu using a Wubi install, it is nearly identical to running it using a native install, meaning, anything that does NOT work under a Wubi install is not suddenly going to work when you do a native install.

You have not been using the Windows drivers; you have been using Linux drivers.

Internet connection is not based on drivers, it's based on networking -- either wired or wireless -- but those devices DO need drivers in order to work.

They use very different drivers and present very different problems, and generally, if you're primarily going to connect via wireless, you need a wired connection to setup, configure, and test the wireless connection.

So, we need to know whether you're going to be connecting primarily through a wired connection or wireless.

Also, to see your network devices, do a "sudo lspci" in a terminal.

---

### Post by sf-it-services on 2010-06-22
I personally always make 4 partitions (including the swap partition), even if only installing linux, I will use one partition for linux and format one other partition as FAT32, I link downloads to this fat32 partition so all downloads remain intact if I get a frozen system in the future.  the spare partition can be used to dual boot at a later date or for more storage if the others become full.

Installation should be something which is structured and defined, this way its possible to understand where everything is, what its doing and what its purpose is.  

That should fix all the wubi/seperate partitions confusion.

At least you made the right decision...... if you don't know, ASK.  I try to teach my employees this, because the only stupid question is the one you realise you didn't ask.

(the fat32 option is just incase you dual boot a windows system, it enables windows to see the partition so you can have the same file store for both OS's)

---

### Post by beelzebufo on 2010-06-23
thanks alot you guys. I reburned a disc image, ran gparted off of my other machine, and installed ubuntu!  Thanks again!

---

