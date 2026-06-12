---
title: "Getting rid of windows dual boot"
date: 2010-11-29
forum: General Help
---

### Post by tommyss4l on 2010-11-29
I just got UNR up and running on my Asus 1018P, I had to use Wubi to get it on here, dual booting UNR and Windows 7. How do I get rid of Windows 7, my computer doesn't want to, or I'm not doing something right to get it to boot from the USB drive.

---

### Post by Tlingit on 2010-11-29
locate the id of the drive you have.

Located in /dev

```
ls /dev
```

then use a general disk utility on that drive you found

```
fdisk /dev/sd(your drive letter here)
```

Then print your partition layout to find out which partition.
```
p
```

then once you know which number it is delete it
```
d
```
after that you can set it to bootable
```
a
```
select the partition number

then you want to write your partition table
```
w
```

after that you will have to use something like
mkfs.ext3 to format the drive.

you can pull that out of 
```
man mkfs.ext3
```

OR!!!!!!!!

```
depending on what distro you are using you can pull up a GUI such as gparted or what ever. delete delete and format the partition
```

hope I helped

---

### Post by miegiel on 2010-11-29
> **tommyss4l said:**
> I just got UNR up and running on my Asus 1018P, I had to use Wubi to get it on here, dual booting UNR and Windows 7. How do I get rid of Windows 7, my computer doesn't want to, or I'm not doing something right to get it to boot from the USB drive.

Are you talking about a wubi installation (no experience with that, sorry) or a normal ubuntu installation in it's own partition?

In any case, on my asus netbook (T101MT) I always install ubuntu from a SD card. I suspect installing from a USB stick works the same, since the card reader is internally connected to a USB port.

In the BIOS boot section there is a boot priority list, listing several boot devices: hard disk, USB FDD, USB CD/DVD rom, network, etc. I don't need to change anything in that list. But there is also an option where you can choose which hard disk to boot from. This is where my SD card is listed as an USB hard disk. To boot from the SD card I just need to put it above the normal hard disk. I suspect that's where you need to select your USB stick too. As soon as I boot without the SD card the normal hard disk moves to the top of the list automatically.

In the installation process you have the option to wipe windows or to install ubuntu next to windows.

---

### Post by wilee-nilee on 2010-11-29
> **tommyss4l said:**
> I just got UNR up and running on my Asus 1018P, I had to use Wubi to get it on here, dual booting UNR and Windows 7. How do I get rid of Windows 7, my computer doesn't want to, or I'm not doing something right to get it to boot from the USB drive.

You can transfer the wubi to a partition, and you can't remove the windows OS that contains it with losing the wubi.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Really if it was me I would just put the wubi in a partition or do a real dual boot then shrink the Windows OS to a use when needed size.

---

### Post by tommyss4l on 2010-11-30
I did install through wubi, that was the only way I could get anything to install. I put the USB drive as the highest priority in the boot menu and the computer just ignored it.

I'll try the SD idea

---

### Post by miegiel on 2010-11-30
> **tommyss4l said:**
> I did install through wubi, that was the only way I could get anything to install. I put the USB drive as the highest priority in the boot menu and the computer just ignored it.

I'll try the SD idea

I still think you're in the wrong place. You shouldn't need to change the "boot device priority". You need to chance the "hard disk drives" list (see pic 1). And then put your USB stick above your hard disk (see pic 2).

Though I have an asus netbook too, it is a different model and I might have a different BIOS. I made the pics with an USB stick in the netbook (can't take pics if the SD card isn't in the camera :roll:)

---

### Post by tommyss4l on 2010-11-30
Ok, I did what you said (our BIOS are the same) and here are the pictures I got. Picture one is the first screen I get, none of the options (except help) are selectable, even after it times out which would automatically live run UNR. The second picture is what I get when I select help. The lines of code at the bottom just keep popping up and stacking every few seconds continuously, the only way I could get rid of them was hitting escape or typing help then hitting enter, which started the process over again.

---

### Post by miegiel on 2010-11-30
> **tommyss4l said:**
> Ok, I did what you said (our BIOS are the same) and here are the pictures I got. Picture one is the first screen I get, none of the options (except help) are selectable, even after it times out which would automatically live run UNR. The second picture is what I get when I select help. The lines of code at the bottom just keep popping up and stacking every few seconds continuously, the only way I could get rid of them was hitting escape or typing help then hitting enter, which started the process over again.

I'm assuming that's your "welcoming" screen as you boot from the USB stick (just making sure I'm not misinterpreting you).

I've never seen a ubuntu installation welcoming screen like that before. Though I have to confess I haven't tried UNR since version 9.04 or so (xubuntu has stolen my heart for a while now). But maybe UNR's welcoming screen is just less pretty. On the second screen it seems like your kernel is misplaced somehow.

Maybe something went wrong putting the .iso on the USB stick. Try putting the .iso on the USB stick again with [this method]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick#Put the installer on a memory stick") (on a windows machine) or [this method]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating a bootable Ubuntu USB flash drive") (on a ubuntu machine). The "windows machine method" was last updated on 2010-06-09, hence it doesn't mention 10.10. But I think that shouldn't cause any problems. Just read "10.04" as "10.04 and/or 10.10".

---

### Post by tommyss4l on 2010-12-01
I'm going with the kernel issue because it's never done that before. 

I'll give it a try on windows, see what happens.
---
ran it on the windows side, gave me a massive amount of things that went wrong, going to re-download the file and try again.
----
It's working now, got a new version of 10.04, wrote it to my USB with pendrivelinux, and everything seems to be working. Thanks a lot for your help.

---

### Post by Prokofiev on 2010-12-28
> **tommyss4l said:**
> I'm going with the kernel issue because it's never done that before. 

I'll give it a try on windows, see what happens.
---
ran it on the windows side, gave me a massive amount of things that went wrong, going to re-download the file and try again.
----
It's working now, got a new version of 10.04, wrote it to my USB with pendrivelinux, and everything seems to be working. Thanks a lot for your help.

Hello, 
Mine isn't working.

I also have an Asus 1018p netbook and tried to install ubuntu netbook throught a pendrive. nothing happened, not even when I switch booting priority on BIOS. My HD has 2 partitions - C and D. Windows 7 is on C, I would like to install Ubuntu on D. 

Tried to run directly wubi.exe, choose installation drive and at the end of 2 hrs it generates and error message saying that it cannot load the downloaded files do continue installation process.

Running through the pendrive I get the metalink error, saing that it "cannot download the metalink and therefore the ISO"...
How can I solve this? Through SD card? 
I'll try running wubi.exe directly on D... considering I tried every other option.

I would appreciate your help.
thanks in advance.

---

### Post by miegiel on 2010-12-29
> **Prokofiev said:**
> Hello, 
Mine isn't working.

I also have an Asus 1018p netbook and tried to install ubuntu netbook throught a pendrive. nothing happened, not even when I switch booting priority on BIOS. My HD has 2 partitions - C and D. Windows 7 is on C, I would like to install Ubuntu on D. 

Did you read what I wrote in posts #3 and #6? I've got the asus eee T101MT, but it worked for **tommyss4l**.

> Tried to run directly wubi.exe, choose installation drive and at the end of 2 hrs it generates and error message saying that it cannot load the downloaded files do continue installation process.

Running through the pendrive I get the metalink error, saing that it "cannot download the metalink and therefore the ISO"...
How can I solve this? Through SD card? 
I'll try running wubi.exe directly on D... considering I tried every other option.

I would appreciate your help.
thanks in advance.

I'm the wrong person to ask about wubi, but if you decide to install ubuntu the "normal" way. It's the easiest to make a empty unformated and unpartitioned space on your disk, either by resizing the partitions (defarg before resizing) or by deleting a partition. The ubuntu installation process will figure out how to partition the empty space for you.

On wubi there's plenty info, just don't ask me ;)

---

### Post by Prokofiev on 2010-12-29
What do you mean by "normal" way? I tried everything... You don't even imagine what happened to my partition. It took hours to install Ubuntu and I had to stop it by the morning because it wouldn't process.... I don't know if I hate Win7 or myself. :mad:
Well...let's forget about wubi. How can I install ubuntu netbook edition (or normal editon) the "normal" way? I think my Asus will never let me to boot D:\ because it says its not bootable...:confused:
Thank you.

---

### Post by miegiel on 2010-12-29
> **Prokofiev said:**
> What do you mean by "normal" way? I tried everything... You don't even imagine what happened to my partition. It took hours to install Ubuntu and I had to stop it by the morning because it wouldn't process.... I don't know if I hate Win7 or myself. :mad:
Well...let's forget about wubi. How can I install ubuntu netbook edition (or normal editon) the "normal" way? I think my Asus will never let me to boot D:\ because it says its not bootable...:confused:
Thank you.

With a normal installation I meant installing ubuntu in it's own partitions instead of doing a wubi installation. As I said I'm no wubi expert. But from what I understand, if you install wubi, it's installed in on one of your windows disks in a file that functions as a virtual partition (or something like that). Wubi is useful for test driving ubuntu or for a temporary installation. But installing updates for ubuntu often breaks the wubi installation, so a "normal installation is a better choice if you want to use ubuntu for a longer time. If you want to know more about wubi read [this]("https://help.ubuntu.com/community/Wubi"). And you can find more info on "wubi problems" in the forum.

Regarding the normal installation, if you managed to select your USB-stick as the first bootdevice/harddisk in the BIOS and you still can't boot from the stick something probably went wrong making the bootable USB-stick. [Here you can find documentation]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") on how to create the bootable USB-stick in windows.

When you boot from the USB-stick you'll get the ubuntu boot screen.
[IMG]https://help.ubuntu.com/community/Installation/FromUSBStickQuick?action=AttachFile&do=get&target=Fig02a.png[/IMG]
If you hit any key at this point you'll get a menu with a couple of choices. Among which, an option to start installing ubuntu, an option to test the CD/USB stick for errors and an to try ubuntu without installing it (yet). The "try ubuntu" option will start ubuntu from the USB stick, this is a useful option if you want to verify if all your hardware will work "out of the box" after installing ubuntu. But it is also useful if you want to connect to a wifi network before you start installing (handy if you want to get updates during the installation). If you select the "try ubuntu" option, you'll find an "install ubuntu" icon on your desktop to start the installation.

The installation process takes (me) about 30 minutes. If you download updates during the installation it can take longer, depending on how fast your internet connection is.

I hope this, together with posts #3 and #6, is enough info to get you on your way.

---

### Post by Prokofiev on 2010-12-30
Thanks a lot miegiel!
I did it! Installed ubuntu through my USB pendrive. I manually partitioned the drivers, lefting the win7 partition untouched. Used a little space to swap, uset a / to mark the space for linux and a /home, I think. Well, I installed Ubuntu but now I cannot boot it. Win7 is untouched, so it's space is fine. When I select My Computer I no longer see drive D:\ (where I supposedly installed ubuntu). It disappeared. If I go to System /advanced options /booting options, windows7 doesn't recognize that's another OS installed in the HDD. 
When I reboot the system I don't get those booting options with win7 and ubuntu at the start of the screen. So... I can tell I "lost" a partition...? 
I'm amazed with things I can do, really..

---

### Post by theozzlives on 2010-12-30
You didn't lose your other partition. Windows don't recognise Linux partitions. Something happened when it came time to install GRUB. Try this [link]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7") to re install GRUB, only you'll boot USB instead of CD.

---

### Post by miegiel on 2010-12-30
> **Prokofiev said:**
> Thanks a lot miegiel!
I did it! Installed ubuntu through my USB pendrive. I manually partitioned the drivers, lefting the win7 partition untouched. Used a little space to swap, uset a / to mark the space for linux and a /home, I think. Well, I installed Ubuntu but now I cannot boot it. Win7 is untouched, so it's space is fine. When I select My Computer I no longer see drive D:\ (where I supposedly installed ubuntu). It disappeared. If I go to System /advanced options /booting options, windows7 doesn't recognize that's another OS installed in the HDD. 
When I reboot the system I don't get those booting options with win7 and ubuntu at the start of the screen. So... I can tell I "lost" a partition...? 
I'm amazed with things I can do, really..

What **theozzlives** said ... and ...

GRUB2 was probably not installed in the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of your harddisk. In the manual partitioning section of the ubuntu installation, at the bottom of the window, you can specify where you want to install the bootloader (GRUB). Ocasionally, when I install ubuntu, the USB disk is selected. But obviously you want GRUB to be installed in the MBR of your harddisk.

As **theozzlives** said, windows doesn't recognize/see linux partitions. So windows won't find a linux installation to add to the windows bootloader.

When you boot from the USB stick and select to "try ubuntu" you can install GRUB2 to your harddisk's MBR. It's possible that you need to make the ubuntu USB stick again if GRUB was placed there when you made your ubuntu partitions. Personally I always use the ["Copy GRUB 2 Files from the LiveCD"]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") method from the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/") site (bookmark that ;)).

When you need to reinstall windows (and occasionally after updating windows) you will need to do the same thing to replace the windows boot loader with GRUB2 again.

---

### Post by Prokofiev on 2011-01-01
Can't do it. Grub is already installed on dev/sda3 and nothing happens. On Win7 I lost my D: and now I cannot recover it. Nice **** I made. I'll try to install another distro, I think, just to see if it works. Thanks anyway

---

### Post by miegiel on 2011-01-01
> **Prokofiev said:**
> Can't do it. Grub is already installed on dev/sda3 and nothing happens. On Win7 I lost my D: and now I cannot recover it. Nice **** I made. I'll try to install another distro, I think, just to see if it works. Thanks anyway

You don't want grub installed to */dev/sda3*, you want it on */dev/sda*.

From "[Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")", did you run :
```
sudo mount /dev/sda3 /mnt
```
Here */dev/sda3* should be your ubuntu root partition.
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Reboot to "try ubuntu" on the USB stick again.
```
sudo update-grub
```
**NB** Make sure before you start, your USB stick and harddisk didn't swap positions, you don't want to do those commands on the wrong disk (happens ocasionally when booting from USB sticks).

---

### Post by Prokofiev on 2011-01-02
Did it, finally!
Thanks a lot guys. Now it's time to explore Ubuntu.
):P

---

