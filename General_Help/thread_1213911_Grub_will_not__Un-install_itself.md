---
title: "Grub will not  Un-install itself"
date: 2009-07-15
forum: General Help
---

### Post by windy81 on 2009-07-15
story so far

i installed Ubuntu on the external hard drive dev/sdb nad installed grub on dev/sdb also.

it worked alright after some tweaking, but then it wouldn't work no matter what i did, so i decided to uninstall ubuntu and do a full format as ntfs so i could use it in XP again.

however, when i start windows with that external hard drive connected, grub still wants to load, and error 17 comes up, and it goes no further in the boot process.

tried recovery mode and fixmbr but it's still the same.

how can i revert the hard drive back to it original state ? i really dont know what else i can do, grub seems embedded in that hard drive now.

tried searching, but no joy

thanks

p.s. i have created a work around by setting windows to boot from cd then internal hard drive, but nevertheless, i would like this fixed properly.

---

### Post by Wim Sturkenboom on 2009-07-15
Did you run fixmbr with a devicename?

source: [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
> 
FIXMBR
fixmbr device name
Use this command to repair the MBR of the boot partition. In the command syntax, device name is an optional device name that specifies the device that requires a new MBR. Use this command if a virus has damaged the MBR and Windows cannot start.

Warning This command can damage your partition tables if a virus is present or if a hardware problem exists. If you use this command, you may create inaccessible partitions. We recommend that you run antivirus software before you use this command.

You can obtain the device name from the output of the map command. If you do not specify a device name, the MBR of the boot device is repaired, for example:
fixmbr \device\harddisk2
If the fixmbr command detects an invalid or non-standard partition table signature, fixmbr command prompts you for permission before it rewrites the MBR. The fixmbr command is supported only on x86-based computers.


---

### Post by windy81 on 2009-07-15
the mbr is a part of the OS, and since there is no OS on the external hard drive any more, i can't see how i could run fixmbr on the external hard drive.

also, i only have one internal hard drive, so i couldn't be a simpler system. i can't understand is why is the grub still there when i've formatted it ?

---

### Post by windy81 on 2009-07-15
[http://ubuntuforums.org/showthread.php?t=1213933](http://ubuntuforums.org/showthread.php?t=1213933)

another person having the same problem. so it could be a Ubuntu wide problem. 

a proper solution would be fabulous.

---

### Post by Wim Sturkenboom on 2009-07-15
Thinking about it, I realize that my post was maybe not the right answer as it will place a MS bootloader in the MBR on the external HD. It might solve the issue or it might not.

> **windy81 said:**
> the mbr is a part of the OS, and since there is no OS on the external hard drive any more, i can't see how i could run fixmbr on the external hard drive.

also, i only have one internal hard drive, so i couldn't be a simpler system. i can't understand is why is the grub still there when i've formatted it ?

The MBR is NOT part of the OS. It's a special place on the harddisk and during the installation of an operating system a bootloader will be placed in there by the installer. 

The MBR is not formatted as it's not part of the partition that you format.

You have 2 MBRs. One on your internal HD and one on your external HD. Your system boots normal (that is what I understand from your opening post) if you do not plug the external HD in as it uses the bootloader that Windows placed in the MBR of your internal HD. If you plug your external HD in and the bootsequence is set to use USB first, it will find the Grub bootloader in the MBR of the external disk and use that.

2 solutions that I can think of:

1)
Use a linux live CD to wipe the MBR. The below code comes from source [http://www.debianhelp.org/node/7310;](http://www.debianhelp.org/node/7310;) replace hda by the device that is your external HD.
```

dd if=/dev/zero of=/dev/hda bs=512 count=1

```

2)
Change the boot sequence in your BIOS so the external HD comes after the internal HD.

---

### Post by windy81 on 2009-07-15
> **Wim Sturkenboom said:**
> Thinking about it, I realize that my post was maybe not the right answer as it will place a MS bootloader in the MBR on the external HD. It might solve the issue or it might not.



The MBR is NOT part of the OS. It's a special place on the harddisk and during the installation of an operating system a bootloader will be placed in there by the installer. 

The MBR is not formatted as it's not part of the partition that you format.

You have 2 MBRs. One on your internal HD and one on your external HD. Your system boots normal (that is what I understand from your opening post) if you do not plug the external HD in as it uses the bootloader that Windows placed in the MBR of your internal HD. If you plug your external HD in and the bootsequence is set to use USB first, it will find the Grub bootloader in the MBR of the external disk and use that.

2 solutions that I can think of:

1)
Use a linux live CD to wipe the MBR. The below code comes from source [http://www.debianhelp.org/node/7310;](http://www.debianhelp.org/node/7310;) replace hda by the device that is your external HD.
```

dd if=/dev/zero of=/dev/hda bs=512 count=1

```2)
Change the boot sequence in your BIOS so the external HD comes after the internal HD.

thanks for your help. 

i didnt know that the mbr wont be registered as part of the partition. 
Thats explains why formatting didnt work and why grub remains.

so i learned something new. ;)

so, i'm going to try solution 1 and i will let you know in a bit.

i have already done solution 2, as a temporary workaround, but i would like the External hdd as it was before i installed ubuntu.

---

### Post by windy81 on 2009-07-15
it says permission denied when i try to execute 

dd if=/dev/zero of=/dev/sdb bs=512 count=1

in terminal

what do i do ?

---

### Post by Wim Sturkenboom on 2009-07-15
If it's an Ubuntu CD, try to put sudo in front of it.

---

### Post by windy81 on 2009-07-15
thats did something, but it still tired to load up from that disk.

however, now, grub seems to be absent, but instead says that a system disk is not present.

anyway, i altered the boot order, which is a working solution, so thanks anyway.

---

### Post by jerome1232 on 2009-07-15
> **windy81 said:**
> thats did something, but it still tired to load up from that disk.

however, now, grub seems to be absent, but instead says that a system disk is not present.

anyway, i altered the boot order, which is a working solution, so thanks anyway.

That means a) it worked and b) your bios was set to boot off of that external drive only

What happened was your bios looked at the boot record of the device it was told to and found a bunch of nothing, it wasn't set to look at any other devices so it came back with that error saying there was nothing to boot.

---

### Post by Wim Sturkenboom on 2009-07-15
> **jerome1232 said:**
> That means a) it worked and b) your bios was set to boot off of that external drive **only**

What happened was your bios looked at the boot record of the device it was told to and found a bunch of nothing, it wasn't set to look at any other devices so it came back with that error saying there was nothing to boot.I don't agree as his systems boots normally when he disconnects the external HD.

---

### Post by Wim Sturkenboom on 2009-07-15
> **windy81 said:**
> however, now, grub seems to be absent, but instead says that a system disk is not present.I wonder if that will not always be the case. But there is still one trick that we can try.
Using the live CD, can you run
```

sudo fdisk /dev/sdb

```
Look for a line that has an '*' under boot (similar to shown below)
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   **[COLOR="Red"]*[/COLOR]**           1        3264    26218048+   7  HPFS/NTFS

```If it's there, you can type 'a' and press <enter> to toggle the 'bootable' flag. It will prompt you for a partition number. Enter the number (probably 1) and press <enter>. Next press 'w' and press <enter> and the change will be written

After this, I'm out of options but please let us know if there was indeed an '*' and if it did the trick. It is possible that it would even have done the trick without wiping the MBR.


==========
Just checked my memory stick that also shows the behaviour and it doesn't have the bootable flag.

---

### Post by windy81 on 2009-07-15
thanks for your help....  

if i recal at the 
```
sudo fdisk -l
```

the bootable flag was not present on the sdb external hard disk.


anyway, I went for a google a while back and it seems that bootable applications such as Active Killdisk are the answer which erases all partitions including partition tables and unseen data via a low level secure deletion format.

i found that Active Killdisk doesn't work on external USb drives so i got this one instead... [http://www.ehow.com/how_4898620_format-external-usb-hard-drive.html](http://www.ehow.com/how_4898620_format-external-usb-hard-drive.html)

im pretty optimistic that'll work since, thanks to you, i understand the problem now.

if however it doesn't, i will try your method.

either way, i'll keep you updated for other users to know.

---

### Post by windy81 on 2009-07-16
no worries, it didn't work, so what, no biggie at the end of the day cos i've set boot to load from Internal HDD instead. Still annoying though

---

### Post by Wim Sturkenboom on 2009-07-20
windy81, can you remember if your PC always wanted to boot from external HD before you installed Ubuntu on it?

I did some tests with USB memory sticks on three PCs
```

+----------+--------------------------------+---------------------+
|          | store_n_go                     | cruzer              |
+----------+--------------------------------+---------------------+
| desktop  | invalid system disk            | boots from HD       |
| acer     | no bootable partition in table | boots from HD       |
| fujitsu  | invalid system disk            | invalid system disk |
+----------+--------------------------------+---------------------+

```
In my opinion, this implies it's a combination of POST and memory stick that determines if a POST wants to boot from HD. None of the sticks that I used for this test, have a bootable partition but there is contents in the MBR.

I wiped the first 446 bytes ofg the store_n_go clean after the test and rebooted using that and the Acer 'hang' without a message. This shows that the code in the MBR is actually executed so the question is why.

I've started a very very long term project to try to analyze the POST so I can understand what is going on.  I'm however not sure if I will ever get any results out of it.

Regards WimS

---

