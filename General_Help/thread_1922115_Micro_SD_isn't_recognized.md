---
title: "Micro SD isn't recognized"
date: 2012-02-08
forum: General Help
---

### Post by iamnigel on 2012-02-08
I use a micro sd card in my Android phone as my mp3 player, and when I put the micro sd card in, Ubuntu doesn't recognize it. It doesn't come up in Nautilus, Banshee, Rhythmbox or the menu thingy on the side. Please help.

---

### Post by satanselbow on 2012-02-08
How are you "putting it in"

Many SD -> microSD adapters are of low quality and sporadic at best. You will get more success with a USB adapter such as:

"Sony Ericsson CCR-80 MicroSD to USB card adaptor" (look it up on amazon)

If you are using a USB cable you also need to mount your card from the android menu ;)

---

### Post by pixiq on 2012-02-08
1. Does it fit in your card reader? I know that some card readers need an adapter for the micro sd card (so that it fits into an ordinary SD card slot).

Install ***hardinfo*** with a GUI, and check if the card reader is found, and if the card in the reader can be found
```
sudo apt-get install hardinfo
```2. Try a terminal command to see if it is recognized as a drive or partition by the operating system:
```
sudo fdisk -lu
```

---

### Post by iamnigel on 2012-02-08
I typed in what you said, and this is what I got:

nigel@nigel-Vostro-3300:~$ sudo apt-get install hardinfo
[sudo] password for nigel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lm-sensors
Suggested packages:
  mesa-utils fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  hardinfo lm-sensors
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 348 kB of archives.
After this operation, 1,204 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe hardinfo i386 0.5.1-1.1ubuntu5 [247 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe lm-sensors i386 1:3.3.0-4ubuntu1 [101 kB]
Fetched 348 kB in 3s (113 kB/s)      
Selecting previously deselected package hardinfo.
(Reading database ... 223945 files and directories currently installed.)
Unpacking hardinfo (from .../hardinfo_0.5.1-1.1ubuntu5_i386.deb) ...
Selecting previously deselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.3.0-4ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up hardinfo (0.5.1-1.1ubuntu5) ...
Setting up lm-sensors (1:3.3.0-4ubuntu1) ...
nigel@nigel-Vostro-3300:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482385919   241191936   83  Linux
/dev/sda2       482387966   488396799     3004417    5  Extended
/dev/sda5       482387968   488396799     3004416   82  Linux swap / Solaris
nigel@nigel-Vostro-3300:~$

---

### Post by pixiq on 2012-02-09
> **iamnigel said:**
> I typed in what you said, and this is what I got:

nigel@nigel-Vostro-3300:~$ sudo apt-get install hardinfo
...

Now that it is installed, you can start hardinfo from the menu system or from the command line with ```
hardinfo
```> 
```
nigel@nigel-Vostro-3300:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482385919   241191936   83  Linux
/dev/sda2       482387966   488396799     3004417    5  Extended
/dev/sda5       482387968   488396799     3004416   82  Linux swap / Solaris
nigel@nigel-Vostro-3300:~$
```Sorry, but fdisk does not see your micro sd card, it sees only the internal HDD.

I'm looking forward to find out if ***hardinfo*** can detect a card reader and a card in that reader.

---

### Post by Mark Phelps on 2012-02-09
Now that laptop manufacturers are including SD slots in their devices, this problem is becoming more prevalent.

Sorry to tell you, but if hardinfo shows that the SD device is not seen, there will be nothing you can do to fix that.  I have a couple of laptops with SD slots, as well as a desktop with a builtin SD device, and they ALL suffer from the same problem.

What I had to do to "fix" it was purchase an external USB-cabled memory card device.  Since it uses a USB slot, it works just fine.

---

### Post by winh8r on 2012-02-09
May I suggest a possible workaround which has worked for me in the past?

I had a small pocket sized digital video camera which worked out of the box with Ubuntu, and never had any issues with being recognised as a device. I always used this camera as a "card reader" when I had problems with other devices not being recognised. If you have a device which you know will be recognised the use it as a card reader, in my experience the device makes no difference and you can access mp3/jpg/mpeg etc on any card inserted into the device.

If connecting a device via USB , an unrecognised device can sometimes be mad to show up using the following method:

Plug the USB cable into a different USB port on your computer (most people use the front ports on desktops, so try it in a rear port)
Leave the device switched on and reboot your computer.

This will usually cause the OS to detect a new storage device and allow access.

I have used this method to access a Panasonic Lumix camera that was consistently not detected when plugged in via USB.

Don't know why it works but it is worth a try.

Good Luck.

---

### Post by gandaran on 2012-02-09
> **iamnigel said:**
> I use a micro sd card in my Android phone as my mp3 player, and when I put the micro sd card in, Ubuntu doesn't recognize it. It doesn't come up in Nautilus, Banshee, Rhythmbox or the menu thingy on the side. Please help.
the android phone does it have a usb storage mode for connecting with PC?
most android phones can mount the SD card drive on PC some others use the MTP method, check how yours works.

---

### Post by Mark Phelps on 2012-02-09
You might note that, in ALL these workarounds (including the one I suggested) the common thread is that they involve using a USB interface.  The USB drivers appear to be able to handle all of these OK.

---

### Post by iamnigel on 2012-02-10
When I put "hardinfo" in a terminal this comes up: 
nigel@nigel-Vostro-3300:~$ hardinfo

(hardinfo:5098): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

I guess I'll get a USB adapter off of Amazon. They're pretty cheap. Thanks.

---

### Post by xyzzyman on 2012-02-10
I've had many issues even with Sandisk MicroSD->SD adapters that came with the MicroSD card. I use my $5 targus reader (It's about the size of a pack of matches) and has a dedicated MicroSD slot on it) and it always works.

---

### Post by brpylko on 2012-02-10
Go into disk utility, if your disk does not show up then it is probably a driver or hardware problem. If it does, then follow these instructions:

In the terminal, run
```

sudo mkdir /media/name_of_device
sudo chmod a+rw /media/name_of_device
sudo mount /dev/sdb /media/name_of_device

```

For this example your device shows up as /dev/sdb in disk utility.

---

### Post by fragos on 2012-02-11
If your card is greater than 2GB it's an SDHC which is physically identical to an SD. If the read is an older SD reader it won't read SDHC cards. SDHC readers will read SD cards. If the card is greater than 16GB it's SDXC I believe and requires the 3rd generation of SD reader.

---

