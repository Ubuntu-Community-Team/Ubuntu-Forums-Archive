---
title: "How to remove Ubuntu???"
date: 2009-06-29
forum: General Help
---

### Post by ruru85 on 2009-06-29
I can hardly find any known safe instructions for removing Ubuntu from my laptop. I am a newbie to this.

I need to remove Ubuntu after installing it in entirely on another portable hard disk. I cannot do a format on the disk as grub will crash if it does not detect Ubuntu. How can i remove grub from the master boot record (MBR).

I am using a HP laptop. Don't think that the system recovery application provided by HP will help to restore the MBR. There is no Windows XP CDs too.

Whats the best way to do this?

---

### Post by t4thfavor on 2009-06-30
download a windows CD. All you need is the recovery console. Boot into that, and issue the fixboot, and fixmbr commands then reboot.

After you are successful open up the computer management disk management snapin and format the ubuntu partition. If you want to then merge the two partitions back together, you will have to use a third party app such as partition magick.

If you want to add it as a logical partition under windows (like a D:\) just create a new partition using NTFS, and call it good.

---

### Post by doas777 on 2009-06-30
you can also use an ubuntu live cd to write a windows mbr
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

ms-sys is no longer in the repos but you can find it here:
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

---

### Post by doas777 on 2009-06-30
> **ruru85 said:**
> I can hardly find any known safe instructions for removing Ubuntu from my laptop. I am a newbie to this.

I need to remove Ubuntu after installing it in entirely on another portable hard disk. I cannot do a format on the disk as grub will crash if it does not detect Ubuntu. How can i remove grub from the master boot record (MBR).

I am using a HP laptop. Don't think that the system recovery application provided by HP will help to restore the MBR. There is no Windows XP CDs too.

Whats the best way to do this?

I believe that the hp recovery will remove the linux mbr, because it recreates the partition itself.

---

### Post by Polaris96 on 2009-06-30
Grub won't crash if it doesn't detect Ubuntu.  You just need to do this:

code:

sudo nano /boot/grub/menu.lst  (or gsudo gedit /boot/grub/menu.lst)
(or kdesu kate /boot/grub/menu.lst)

then change this:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0


You need to change the number at the very end of the last line (default 0) to the menu choice that says "Windows"  (make sure there are no #s in front of the menu choices you are counting - there's a "sample menu" in menu.lst.  don't be confused)

After that, you can leave grub and just add your new Linux device to the grub list after you install Ubuntu on your new drive.  You can then delete the old linux partition with the app of your choice. TEST THE CHANGES YUO MADE TO GRUB BEFORE YOUR DELET THE LINUX PARTITION.

---

