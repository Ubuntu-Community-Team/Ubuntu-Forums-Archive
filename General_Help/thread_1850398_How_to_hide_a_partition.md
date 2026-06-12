---
title: "How to hide a partition?"
date: 2011-09-26
forum: General Help
---

### Post by sakibmoon on 2011-09-26
Is there a way to hide a partition in Ubuntu?

I have a dualboot Windows 7 with Ubuntu. There is a system reserved partition of Windows 7. I want to hide this partition.

---

### Post by Frogs Hair on 2011-09-26
Here is one solution I found  , but I  have not tried it .

1.Go to Ubuntu Software Center
2.Under system search for Gnome Partition Editor and install it
3.System->Administration->GParted
4.Right click on the system reserved partition and click manage flags
5.Check hidden

---

### Post by Morbius1 on 2011-09-26
[1] Run the following command to get the correct uuid number:
```
sudo blkid -c /dev/null
```You'll get something that looks like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" [2] Make a mount point:
```
sudo mkdir /Win7Res
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line at the bottom of the file:
```
 UUID=DA9056C19056A3B3 /Win7Res ntfs noauto,umask=277,ro 0 0
```[5] Run the following command to test for errors and reinitialize fstab:
```
sudo mount -a
```It's not going to hide it. The /Win7Res directory will still be visible in the file manager but it will be empty.

---

### Post by matt_symes on 2011-09-26
Hi

You can also hide a partition using udev.

Open a terminal and type

```
sudo nano /etc/udev/rules.d/hide-partitions.rules
```Copy this into the file.

```

ACTION!="add|change", GOTO="hide_partition_end"
SUBSYSTEM!="block", GOTO="hide_partition_end"
KERNEL=="loop*|ram*", GOTO="hide_partition_end"
KERNEL=="**sda2**", ENV{UDISKS_PRESENTATION_HIDE}="1"
LABEL="hide_partition_end" 
```Change sda2 for the partition you want to hide, then reboot your pc. Hopefully that will hide your partition. I used to use this method to hide my windows recovery partition.

Kind regards

---

### Post by dcstar on 2011-09-27
> **sakibmoon said:**
> Is there a way to hide a partition in Ubuntu?

I have a dualboot Windows 7 with Ubuntu. There is a system reserved partition of Windows 7. I want to hide this partition.

Add the partition to the /etc/fstab file and add in the "noauto" option (use the **pysdm** package to do this).

That way it can only be mounted by a specific terminal command and will therefore be "invisible" until that occurs.

---

### Post by Morbius1 on 2011-09-27
Although all of these are legitimate options I would caution you about the use of pysdm. It is no longer maintained ( none of these gui utilities for editing fstab are maintained any longer ) and is dated. 

It is incapable for example of identifying partitions by UUID or LABEL which is the current recommended standard for fstab entries and has some options missing for ntfs in particular.

If you feel compelled to to use pysdm anyway don't forget to make a copy of your current fstab as the utility does not make a copy by itself and you may need it if you want to restore your system:
```
sudo cp -a /etc/fstab /etc/fstab.bak
```

---

### Post by sakibmoon on 2011-10-14
Thanks a lot guys.

---

### Post by jhall124 on 2011-10-17
> **Frogs Hair said:**
> Here is one solution I found  , but I  have not tried it .

1.Go to Ubuntu Software Center
2.Under system search for Gnome Partition Editor and install it
3.System->Administration->GParted
4.Right click on the system reserved partition and click manage flags
5.Check hidden

This also works for stopping SD cards from mounting.
Thanks for the post, you rock !!!
:p

---

