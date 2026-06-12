---
title: "Unable to boot Windows"
date: 2009-07-17
forum: General Help
---

### Post by kelleytheboy on 2009-07-17
Hello, I recently installed windows and followed all of the steps in the 9.04 installation. Now I can't boot windows, the files for windows however are still there when I boot into Ubuntu, the documents, the OS etc. Please help, are the instructions on [this page]("http://www.howtoforge.com/working_with_the_grub_menu") the solution? 
Thanks

---

### Post by NightwishFan on 2009-07-17
When you try to boot windows, what does it say?

EDIT: I believe you can automatically repair grub in the Jaunty recover mode.

---

### Post by kelleytheboy on 2009-07-17
it doesn't say anything i the way of error messages. however when I select to boot into windows the display stays in the black and white mode and reads "starting up". It stays like this for as long as you let it. sorry i didnt reply earlier i thought it would take longer. also has anyone followed the hyperlink in the first post.

---

### Post by oldfred on 2009-07-17
Did you literally follow the directions on the link. His Windows partition was disk 1, partition number 3 so his line in menu.lst was root   (hd0,2).

To get a list of your drives & partitions: 
sudo fdisk -l             

One line should look like this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7179    57665286    7  HPFS/NTFS

This is my windows partition on disk 1, so my menu.lst has this entry:
# This is a divider, added to separate the menu items below from the # Debian ones.
#title        Other operating systems:
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Grub partitions are numbered one less than linux - sd[COLOR=Red]a1[/COLOR] in linux is (hd0,0) in Grub, sd[COLOR=Red]a2[/COLOR] is (hd0,1) , sd[COLOR=Red]b1[/COLOR] is (h1,0) etc 
Check to make sure you have the correct boot partition. If you need further help post your fdisk -l output and your menu.lst.

---

### Post by kelleytheboy on 2009-07-17
I havent followed the instructions i was woundering if they would work. here is the info you asked for.
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28970   232701493+   7  HPFS/NTFS
/dev/sda2           29297       30401     8875440    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           28971       29296     2618595    5  Extended
/dev/sda5           28971       29274     2441848+  83  Linux
/dev/sda6           29275       29296      176683+  82  Linux swap / Solaris

---

### Post by oldfred on 2009-07-17
Your windows boot drive is exactly like mine. You can follow the directions on the link, but [FONT=monospace]       use (hd0,0)[/FONT] But all you should have to do is edit the menu.lst to match mine if yours is different. If the boot sector is messed up you may also have to use grub to repair it but first check menu.lst and see if this works.
[FONT=monospace]
 and backup first, just in case:
sudo cp [/FONT][FONT=monospace]/boot/grub/menu.lst[/FONT] /boot/grub.menu.lst.backup
[FONT=monospace]gksudo gedit /boot/grub/menu.lst
 
near the bottom should be your windows boot, modify it to match this or paste this in your menu.lst:

title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1
[/FONT]

---

### Post by kelleytheboy on 2009-07-17
I did this and the two were the same. Any other suggestions

---

### Post by oldfred on 2009-07-18
Are you getting a GRUB error or is it that the windows ndltr is missing. 
Use the super grub disk/cd to fix grub errors or your windows cd to repair the windows install. I am not familiar with the exact commands as I never had this problem with my dual, now multiboot of Windows, Ubuntu 32 and now Ubuntu 64.

---

### Post by ptsubin on 2009-07-18
I would suggest an option. This seems your grub is fine. And problem may be with windows startup. Insert windows XP cd and boot in to it. Enter the recovery console by pressing R when it asks you to install a new copy or repair an existing one. When you get the command prompt, type **fixmbr** there. Then also type **fixboot** after fixmbr completes. Then your grub will be gone and see if you are able to start windows by rebooting. 

Now to restore the grub loader, put the Ubuntu live cd and start ubuntu. open a terminal and type 
sudo su root
mount the linux root partition. I guess it is sda5 from the above fdisk -l output.Then 
grub /dev/sda5
you will get the grub shell
grub> find /boot/grub/stage1

it will give you the partition number if root partition is mounted. possibly (hd0,4)
now,
grub> root (gd0,4)
grub> setup (hd0)
This will reinstall grub with the settings in menu.lst
grub> quit
reboot

Hope this will work. This can even work if you reinstall your windows.

---

### Post by vinutux on 2009-07-18
> **ptsubin said:**
> I would suggest an option. This seems your grub is fine. And problem may be with windows startup. Insert windows XP cd and boot in to it. Enter the recovery console by pressing R when it asks you to install a new copy or repair an existing one. When you get the command prompt, type **fixmbr** there. Then also type **fixboot** after fixmbr completes. Then your grub will be gone and see if you are able to start windows by rebooting. 

Now to restore the grub loader, put the Ubuntu live cd and start ubuntu. open a terminal and type 
sudo su root
mount the linux root partition. I guess it is sda5 from the above fdisk -l output.Then 
grub /dev/sda5
you will get the grub shell
grub> find /boot/grub/stage1

it will give you the partition number if root partition is mounted. possibly (hd0,4)
now,
grub> root (gd0,4)
grub> setup (hd0)
This will reinstall grub with the settings in menu.lst
grub> quit
reboot

Hope this will work. This can even work if you reinstall your windows.

yeh...this reinstalling grub may work 4 u

---

