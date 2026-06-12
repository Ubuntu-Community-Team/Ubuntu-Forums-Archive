---
title: "Helpful commands to get all hardware info?"
date: 2009-12-08
forum: General Help
---

### Post by MountainX on 2009-12-08
I am interested in a list of ***all*** common commands related to discovering system hardware information (maybe with brief explanations). 

I started by searching for a list of widely used trouble shooting commands or a FAQ. I didn't find one. Surely something like that must exist. I did not find it yet. Until I do, I'll start such a list by mentioning a few "hardware discovery" commands I know:

[LIST]
[*][lspci]("http://www.linuxguide.it/command_line/linux-manpage/do.php?file=lspci")
[*][lsusb]("http://www.linuxguide.it/command_line/linux-manpage/do.php?file=lsusb")
[*]dmesg
[*]lshw
[*]dmidecode
[/LIST]
The last one (**dmidecode**) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command. It was already available in my install of Mythbuntu 9.10 as well as in Ubuntu 9.04 on my desktop.

I ran it like this:
```
sudo dmidecode | less
```

**udevadm** is another powerful tool for discovering hardware info. Here's a doc that gives a nice [udev overview]("http://www.reactivated.net/writing_udev_rules.html") (although the purpose of the doc is writing udev rules).

The straightward way to use it is:
$ sudo udevadm info -a -p */devices/path *
(example only - needs real path info to run)

Here's an actual example:
```
sudo udevadm info -a -p /devices/pci0000:00/0000:00:02.1/usb1/1-3/video4linux/video1
```However, as you can see, we often do not have the full path info required to run the command this way. (I certainly would not have had the path shown above already in hand.) The easier alternative is to do this:
```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/video1)
```This syntax is explained to the best of my ability [*here*]("http://ubuntuforums.org/showpost.php?p=8480216&postcount=4") (comment 4 below)

There are a bunch of helpful commands related to storage and the filesystem too. Here are a few I use:

[LIST]
[*]df -h (lists by GB)
[*]fdisk -l
[*]sudo blkid
[*]sudo ls -l /dev/disk/by-uuid
[*]sudo lshw
[/LIST]
 
Here is an excellent script that generates lots of disk and boot-related info:
**sudo bash boot_info_script27.sh  **
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
See [http://ubuntuforums.org/showpost.php?p=6811432](http://ubuntuforums.org/showpost.php?p=6811432)

See [http://www.linuxguide.it/linux_commands_line_en.htm](http://www.linuxguide.it/linux_commands_line_en.htm) for a table of other helpful system commands

EDIT: My [*original*]("http://ubuntuforums.org/showpost.php?p=8480216&postcount=4") question was how do I find out which video capture card is mapped to which device node? That is solved now. See comment 4.

---

### Post by dcstar on 2009-12-09
> **MountainX said:**
> My *immediate* question: how do I find out which video capture card is mapped to which device node? However, I am also looking for a list of all helpful commands related to system hardware.

I am playing around with MythTV and I need to find out which video capture cards are mapped to which devices nodes (e.g., /dev/videoN). I'm looking for a command that will let me do this in an SSH shell.
........

Try hwinfo.

---

### Post by MountainX on 2009-12-11
Here's one more tool: Usbview
[http://www.kroah.com/linux/usb/](http://www.kroah.com/linux/usb/)

> USBView is a GTK program that displays the topography of the devices that are plugged into the USB bus on a Linux machine. It also displays information on each of the devices. This can be useful to determine if a device is working properly or not.

---

### Post by MountainX on 2009-12-11
**SOLVED**: Answer to my original question: **how do I find out which video capture card is mapped to which device node?**

```
ls /dev/vid*
```/dev/video0  /dev/video1  /dev/video24  /dev/video32

```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/video1)
```looking at device '/devices/pci0000:00/0000:00:02.1/usb1/1-3/video4linux/video1':
    KERNEL=="video1"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="au0828a video"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-3':
    KERNELS=="1-3"
    SUBSYSTEMS=="usb"
    [snip]
    ATTRS{manufacturer}=="Hauppauge"
    ATTRS{product}=="**WinTV HVR-850**"


The above udevadm info command told me that /dev/video1 is my WinTV HRV-850. Doing the same thing for video0 only indicated it was an "ivtv0 encoder MPG" device with ATTRS{vendor}=="0x4444", and my experience (or Google) told me that this was the PVR150.

I'll offer a few comments on this rule:
```
udevadm info -a -p $(udevadm info -q path -n /dev/video1)
```According to Scott James Remnant, "udevadm info is safe to call, and in recent releases returns all information; combining both the udevdb and the kernel uevent info."

_-a is short for --attribute-walk_
Print all sysfs properties of the specified device that can be used in udev rules to match the specified device. It prints all devices along the chain, up to the root of sysfs that can be used in udev rules.

_-p is short for --path=devpath_
The devpath of the device to query. Symlinks are not valid.

However, /dev/video0 is a type of symlink (a "character special file"):
$ ls -la /dev/video0
crw-rw----+ 1 root video 81, 0 2009-12-09 23:35 /dev/video0

The real path is:
/devices/pci0000:00/0000:00:02.1/usb1/1-3/video4linux/video1
But we usually don't know that. So we use a udevadm query to handle those details for us.

_-q is short for --query=type_
Query the database for specified type of device data. It needs the --path or --name to identify the specified device.

_-n is short for --name=file_
The name of the device node or a **symlink** (e.g., /dev/video1) to query.

---

### Post by falconindy on 2009-12-11
You might also be interested in making udev rules so that you can expect a certain card to be attached a certain node.

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

