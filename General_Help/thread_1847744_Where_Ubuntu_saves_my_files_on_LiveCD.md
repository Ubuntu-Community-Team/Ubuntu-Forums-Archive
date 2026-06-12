---
title: "Where Ubuntu saves my files on LiveCD?"
date: 2011-09-21
forum: General Help
---

### Post by papaapa on 2011-09-21
Hello!

I could not find where Ubuntu (or any Linux distro) saves the files which i copy them on home folder when i use LiveCD? On my HDD? or on RAM? (I don't think that it saves on RAM, because last time i downloaded from internet about 600 MB file, "gnome-system-monitor" show me that i even don't use 600 MB of RAM yet.)

Thank you!

---

### Post by Trubbelgum on 2011-09-21
I thought Ubuntu temporary stored the data on the RAM, because you can run the Ubuntu Live CD without hard drive. 

Maybe the Ubuntu Live CD reserves let's say 2GB of RAM, to use like a hard drive and then these 2GBs aren't shown as used RAM.

---

### Post by t0p on 2011-09-21
The LiveCD saves stuff to the Downloads folder by default, I think.  But this is *not* the Downloads folder on your computer's hard drive, it saves it to the liveCD file system which is in RAM, and which will disappear when you shut down.

If you want downloaded files to keep, get a USB stick or similar, and specifically tell Ubuntu to save to that.

---

### Post by papaapa on 2011-09-21
> **Trubbelgum said:**
> I thought Ubuntu temporary stored the data on the RAM, because you can run the Ubuntu Live CD without hard drive. 

Maybe the Ubuntu Live CD reserves let's say 2GB of RAM, to use like a hard drive and then these 2GBs aren't shown as used RAM.

No It shows me all my memory. And it does not increase the total of using memory.

---

### Post by YesWeCan on 2011-09-21
The System Monitor doesn't report how much total RAM is being used. Try running 'watch free' in a terminal and observer the amount of free space change as you download a large file.
Same thing if you make a RAM disk the System Monitor won't show it.

---

