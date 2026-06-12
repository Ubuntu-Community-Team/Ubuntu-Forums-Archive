---
title: "partition editor"
date: 2010-05-08
forum: General Help
---

### Post by subcook on 2010-05-08
For the life of me I cannot find the partition editor in 10.4

I am trying to reset the (boot partition) flag.

Where can I find the partition editor.

looking for a very easy answer to a very easy question

thank you


-cheers

---

### Post by jscherer92 on 2010-05-08
Well the one I use is call GParted. It does all that you are looking for. If it is not under Ubuntu Software Center, it is under Synaptic Package Manager. I hope this helps!

- Justin -
[http://tutorials-for-all.dyndns.org.x10hosting.com](http://tutorials-for-all.dyndns.org.x10hosting.com)

---

### Post by srs5694 on 2010-05-08
There are several. There should be a link in the GNOME menu to GParted or some other GUI tool, but I don't know the exact path offhand. (I don't use GNOME much, and the system I'm using now runs Gentoo.)

If you open a Terminal, xterm, Konsole, or whatever, you can launch several from it:


[list]
[*]**gparted** -- launches GParted (GUI)
[*]**parted** -- launches GNU Parted (interactive or command-line text-mode)
[*]**fdisk** -- launches Linux fdisk (interactive text-mode)
[*]**sfdisk** -- launches Linux sfdisk (command-line text-mode)
[*]**cfdisk** -- launches Linux cfdisk (interactive text-mode)
[/list]


Some of these require you to type a device name (such as /dev/sda) on the command line. These all edit Master Boot Record (MBR) disks, which is presumably what you've got since you mention the boot flag. There are also a few other tools that are based on libparted. GParted and GNU Parted can also handle GUID Partition Table (GPT) disks, but they don't have boot flags. The gdisk and sgdisk programs (part of the gdisk package in 10.04) also handle GPT disks.

---

### Post by ranch hand on 2010-05-08
If you are doing anything on a drive it is best to do this from the Live CD where you will find Gparted at System>Administration>Gparted.

---

### Post by lmarmisa on 2010-05-08
Open Synaptic and install GParted. 

GParted is included in the LiveCD but not in the standard installation of Ubuntu.

---

### Post by subcook on 2010-05-11
thanks for the help everyone,  that helps !!


-cheers

---

