---
title: "New user, major problem"
date: 2009-11-13
forum: General Help
---

### Post by Mike The Bard on 2009-11-13
Installed Ubuntu 9.1 on my old Dell Inspiron 8200.  Love it.  Great all the way around.

Then, as far as I can tell, a sector crapped out on my hard drive, and I can no longer boot into Linux.  I can still boot into Windows, or with my Ubuntu boot disc.  I'm sure that reinstalling will work fine, but-
[B]
Is there a way I can recover my data?[/B]  I had a few documents that weren't backed up yet, and I'd love to be able to recover my preferences and whatnot.

Please help...?

---

### Post by Ms_Angel_D on 2009-11-13
Use the live cd to back your files up ;)

---

### Post by Mike The Bard on 2009-11-13
That was my general plan- Again, I apologize for sounding like an idiot, but I can't tell which files I'm looking for.

I installed Ubuntu along side of Windows XP.  When I boot from the live CD, I can open my HD.  If I open the windows or Documents folders, I can see all my windows stuff- There's also an "Ubuntu" folder on the drive, but nothing in it that I recognize as my files or familiar folder structure.

I can see folder named "disks" with a "root.disk" file that's quite large, but I can't see inside it- I tried using the archive viewer and mounter, but to no avail.

---

### Post by Ms_Angel_D on 2009-11-13
Did you actually install in a separate partition? To me it sounds like you installed using wubi, if that's the case then I'm not really sure how to get your files.

Wubi is great to try out Ubuntu I don't recommend using it full time in place of an actual partition.

---

### Post by Ravernomina on 2009-11-13
Go on Windows and go into your ubuntu folder in programs
download virtual box
find the ubuntu image made by wubi
have virtual box load the image and get your data

---

### Post by nawtion on 2009-11-13
I never used wubi, but I think your best bet as far as recovering data is to use a live cd and copy your home folder (\home\"username").  I'm not sure about preferences...but you should get all your documents, etc.

Also, if you think the problem is your boot loader, [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html), is a tutorial for reinstalling grub.  I would just make sure to back up my grub settings, in case if re-installing grub causes you to loose the windows boot option in the grub menu.  Read [this article]("https://wiki.ubuntu.com/Grub2") if you have GRUB 2 (1.97), since the settings are different. In older GRUB versions, the file is found at /boot/grub/*menu*.*1st*

---

### Post by Mike The Bard on 2009-11-14
Yeah, I used the Wubi installer, and like I said- When I open the Ubuntu folder, there's no "home", no "applications", no "mike" nested anywhere inside.  It looks like everything is packed inside some sort of wrapper at C:>UBUNTU>DISKS>ROOT.DISK

I'm going to try reinstalling Grub and see if that works....

---

### Post by Ms_Angel_D on 2009-11-14
> **Mike The Bard said:**
> Yeah, I used the Wubi installer, and like I said- When I open the Ubuntu folder, there's no "home", no "applications", no "mike" nested anywhere inside.  It looks like everything is packed inside some sort of wrapper at C:>UBUNTU>DISKS>ROOT.DISK

I'm going to try reinstalling Grub and see if that works....

Wubi doesn't install grub, it adds an entry to the windows boot loader. Be careful I would hate to see you mess up your windows install as well.

---

