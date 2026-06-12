---
title: "Access Extra Storage Space on a Ubuntu Booting USB drive?"
date: 2011-01-20
forum: General Help
---

### Post by bbczju on 2011-01-20
Hi everyone. I've installed the 10.10 desktop edition on my 8GB FAT32 usb-drive using the universal usb installer downloaded from the official website, with the option of a 4GB persistence space. 

However the remaining available space is by no means accessible in Ubuntu if I boot from my usb-drive (though I could see it in Windows).

 Is there any ways to work around this? Do I need some sort of software to do that? I've searched the web without a definitive answer. Thanks a bunch! :KS

Ray
Jan.20th 2011

---

### Post by efflandt on 2011-01-20
Did you try opening **Places** (nautilus) and see if it auto mounts when you click on it? Of course your persistence (casper-rw file) and iso files would use about 4.7 GB of it.

---

### Post by bbczju on 2011-01-22
> **efflandt said:**
> Did you try opening **Places** (nautilus) and see if it auto mounts when you click on it? Of course your persistence (casper-rw file) and iso files would use about 4.7 GB of it.
Thank you for your reply efflandt.

I've checked the 'Places' menu and couldn't see my usb drive there. Then it occurs to me that 'Disk Utility' might know something. And I find out the whole drive is actually mounted at location /cdrom :p problem soloved!

Sorry for this newbie question. Thanks ag :)

---

