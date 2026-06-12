---
title: "Cannot Delete Partition Because of Mounted Partition"
date: 2011-12-28
forum: General Help
---

### Post by dancapp on 2011-12-28
Hey everyone. I currently have KXStudio (kubuntu), Windows Vista (:-&) and Tango Studio installed. Tango is /dev/sda6 and I don't need it anymore, but when I try to delete it I get this error message:

> The partition /dev/sda6 cannot currently be deleted because one or more partitions with higher logical numbers are still mounted. 
Please unmount all partitions with higher logical numbers than 6 first.

It's probably simple stuff but I have no idea what this means or how to solve it. Any help would be greatly appreciated and I've attached a screenshot of KDE Partition Manager. Thanks.

-Dan

---

### Post by sohmc on 2011-12-28
Just like the error says, you should unmount /dev/sda8 and /dev/sda7 first before unmounting /dev/sda6.  Once you delete /dev/sda6, you can remount 7 and 8.

---

### Post by dancapp on 2011-12-28
8 is my KXStudio installation (which I'm currently using) and it looks like I have to unmount this before I can unmount 7, and so on. Is there any danger in unmounting an installation and do I have to be using a different OS to unmount the one I'm currently on?

Thanks for your help!

---

### Post by pretty_whistle on 2011-12-28
> **dancapp said:**
> 8 is my KXStudio installation (which I'm currently using) and it looks like I have to unmount this before I can unmount 7, and so on. Is there any danger in unmounting an installation and do I have to be using a different OS to unmount the one I'm currently on?

Thanks for your help!
Yes you should use another system.  It probably wouldn't let you unmount something you're using while using it.

---

### Post by Synoc on 2011-12-28
you should be able to use the Live CD unmount, this may alter grub2's behavior. I don't know if it will update

---

### Post by sohmc on 2011-12-29
It would only alter grub2's behavior if the partition number was changed, which it shouldn't be.  Again, SHOULDN'T.  If it does, you'll have to put in a dummy partition.  Give it 8MB or something so that it can hold onto the space.

---

### Post by alphaamanitin on 2011-12-29
Get a liveCD of GParted and boot from that.  You can then delete partitions and the like to your hearts content.  Don't know if it would matter in your situation but you might need to turn off any swap partition you have because GParted uses this to speed up deleting/moving/resizing partitions and this sometimes prevents you from manipulating extended partitions if they contain the swap.

Also, you don't need to put in a dummy partition.  Simply boot into a live version of ubuntu mount the drive in question chmod into that mount and update grub, that should fix any grub issues.

AlphaA

---

