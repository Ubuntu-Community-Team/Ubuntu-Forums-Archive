---
title: "Unable to mount usb drives"
date: 2010-05-17
forum: General Help
---

### Post by stoneage on 2010-05-17
Ubuntu 9.10 64 bit

Can't mount external usb drives. There are no errors, they just don't show up anywhere. 

Also Trash icon has disappeared from bottom panel, is inaccessible from Nautilus - "Sorry, could not display all the contents of "trash": Operation not supported" - and Desktop icons default to 'Keep Aligned' every time I restart.

etc/fstab with a flash drive and an external HDD plugged in:-
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b2d8cbb3-2673-4a9e-86e5-41c5e6458f84 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0b122412-75af-4cd5-aa18-a55303b302d9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



EDIT - ok, I have found the cause. It is related to installing a non-repo version of glib while compiling Gimp. I don't know the easy way to fix it, but I should be able to sort it one way or another. 

 ```
sudo mv /usr/local /usr/local.old
``` 
```
sudo mkdir /urs/local
``` and restarting seems to have resolved everything. 

Suggestions still welcomed... :)

---

### Post by 2hot6ft2 on 2010-05-17
> **stoneage said:**
> Ubuntu 9.10 64 bit

Can't mount external usb drives. There are no errors, they just don't show up anywhere. 
open a terminal and use
```
gconf-editor
```
and go to Apps > Nautilus > Desktop > volumes visible
(you will also see trash icon visible there too for the desktop)
then they will show up on the desktop.
If that's not the issue try this
```
sudo apt-get install systemsettings

```
1. On top menu bar goto System --> Preferences --> System Settings
2. A Systems Settings Window will pop-up
3. On the Systems Settings Window click on the 'Advanced' Tab (the other one is 'General')
4. On the section 'Advance User Settings' look for 'Removable Devices' and click on it
5. This will take you to Removable Devices - System Settings Window.
6. Click 'Enable automatic mounting of removable media'
> **stoneage said:**
> Also Trash icon has disappeared from bottom panel, is inaccessible from Nautilus - "Sorry, could not display all the contents of "trash": Operation not supported"
Right click the bottom panel and select Add to Panel and select Trash then Add and Close
or you can reset the panels to their default.
Use Alt+F2
and follow these instructions (**be very careful with the second one**)
> **lidex said:**
> Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
There's a start.

---

### Post by stoneage on 2010-05-17
Thanks :)

> **2hot6ft2 said:**
> open a terminal and use
```
gconf-editor
```
and go to Apps > Nautilus > Desktop > volumes visible
(you will also see trash icon visible there too for the desktop)
then they will show up on the desktop.
Already tried this - no joy


> **2hot6ft2 said:**
> 
Right click the bottom panel and select Add to Panel and select Trash then Add and Close
or you can reset the panels to their default.
Use Alt+F2
and follow these instructions (**be very careful with the second one**)

There's a start.
Already tried this - no joy

You did read the EDIT didn't you ? :)

---

