---
title: "Ubuntu will only boot with my second hard disk unplugged. (Linux amateur)"
date: 2011-03-26
forum: General Help
---

### Post by R4a2m0o on 2011-03-26
I have two 320gb seagates.  They are identical.  If I have both plugged in, the OS runs into an error during bootup.  With only the install drive and the DVD drive it boots up, hence this posting.  I forget the exact wording but it asked me to increase the wait time for the boot disk to respond or to specify a different boot disk.  

I am convinced that I need to edit the GRUB bootloader deal to point at the correct drive by saying /dev/sda but I have absolutely no clue how to do it.  I don´t even know how a hard drive gets assigned a name, whether it is static or whatever.  I am a complete noob when it comes to Linux but I´m good with computers and I want to learn.  

As a secondary problem, I am getting ready to install 2 additional drives, both 2TB each.  What do I need to do to get the OS to accept it them, name them, identify them, or whatever needs to happen.

---

### Post by garvinrick4 on 2011-03-26
Is one internal and one external USB? If the second disk has to be unplugged and it
USB device then you have USB to boot first in order in BIOS. Change it to HDD so the
internal boots first and you should see both.
Now if second drive has no operating system it will mount as a drive. If it has a operating
system need to.
```
sudo update-grub
```
after internal boots to add it to grub config file and make a menu item to boot from.

---

### Post by garvinrick4 on 2011-03-26
adding additional drives will show up under Places drop down menu and if you want you can have them automount or not. If they have Operating Systems installed have to update-grub to have them put in grub-menu. Drives just get different numbers first is sda
second sdb third sdc and so on and so on. If you get in a pickle just download this script
to your Desktop and run code below:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```
Will put a text file on Desktop called Results that will have your whole
boot info in it. Users can fix you up in a second or two.

---

### Post by R4a2m0o on 2011-03-26
Thanks for the tips.  I took the second drive out, and put in my 2x2Tb storage disks and they recognized and booted up into the GUI just fine.  Now there is only one slight issue where it says only 3/4 metada areas found on dev/sda.  Then it thinks for a bit, then boots.

Also, on the GRUB screen during bootup, after I did the rebuild GRUB command in the terminal like you told me to, there is now a new version showing up in grub ending in 28 rather than 22.  Is that any cause for concern?

---

### Post by R4a2m0o on 2011-03-26
I just looked for the 2 hard disks I added and I can´t see them when I open computer.  What do I need to do to format them and make them visible?

---

### Post by garvinrick4 on 2011-03-26
Look in places drop down menu in upper left of top toolbar.
Should be there.

And there will always be new versions of kernels coming out that are
added to your grub menu entries.

---

### Post by R4a2m0o on 2011-03-26
Don´t see them.  These are brand new hard disks just unpackaged.  I want to use them for backup.  They are unformatted...  

In fact I don´t even know how to view my boot drive.  Free space and all that jazz.

---

### Post by woodmaster on 2011-03-26
open a terminal, type 
> sudo apt-get install gparted
then you will need to type your password(nothing will show as you type, this is normal behaviour)
started should now be listed under your administration menu.  This will allow you to see all your disks, their partitions, and their usages...

---

### Post by garvinrick4 on 2011-03-26
* This two packages are disk partitioning and formatting packages be careful and focus.

In System/Administration to Disk Utility:
Open Disk Utility and click on drive you want to format:
Format to NTFS if for Data.

If not there then:
```
sudo apt-get install gparted
```Will be in same place System/Administration
In upper right corner of gparted window can choose between all drives;
Once you choose which drive you can right click on and format then hit 
green apply arrow to execute. 

If you want to automount at boot to desktop:
Alt/F2
 type    gconf-editor  in box: Hit run:
Go to Apps/Nautilus/preferences and will give you media_automount and media_automount_open boxes to check if desired.

---

