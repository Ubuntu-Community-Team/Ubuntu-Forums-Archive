---
title: "USB to USB connection?"
date: 2006-04-29
forum: General Help
---

### Post by mztriz on 2006-04-29
Okay here's what I would loveeee to do.

I have two computers, connected to eachother right now, via USB.
One computer; the one I am currently on, is running off of the Ubuntu Live CD, the other computer has Ubuntu installed.

What I want to do is access the Ubuntu computer from the Live CD computer in order to copy an image over it's harddrive. Is this possible? 

Thanks everyone,
Ava

---

### Post by az on 2006-04-29
You are using a special cable to connect two boxes through usb?  I beleive there are linux modules for that in the kernel and your usb connection just appears as a regular ethernet connection.  Is this what you have?

You would want to copy the ubuntu partition from the box where it is installed to the box where you are running the live cd?  You could partition the disk and then use ssh, ftp, nfs or samba to copy all the files to the new box.  Then just adjust /etc/fstab and /boot/grub/menu.list and run 
sudo grub-install

---

