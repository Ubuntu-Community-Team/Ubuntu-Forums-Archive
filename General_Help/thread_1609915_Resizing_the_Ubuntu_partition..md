---
title: "Resizing the Ubuntu partition."
date: 2010-10-31
forum: General Help
---

### Post by Omnomnom on 2010-10-31
When I run out of space on my Ubuntu partition, which will probably happen with me being the untidy person I am, is there a way to resize the partition in Windows or Ubuntu that will allow the other to boot? As I've heard stories of using Gparted to resize a Windows partition doesn't allow Windows Vista to boot up as it removes a crucial part of the operating system? Could someone enlighten me please, because I have adequate space to give to Ubuntu on my NTFS partition. May I also add that to install Ubuntu I had to use the partitioner that came with the installer, because the Windows Disk Manager wouldn't let me partition the NTFS drive, because it Denied my Access.

Thanks in advance, Nom.

---

### Post by Omnomnom on 2010-10-31
Bump

---

### Post by garvinrick4 on 2010-10-31
Anytime you want to resize a Windows partition just defrag, defrag and defrag again to make sure all is tidy before you make any changes. I like gparted the best, I even download an .iso file of it and burn it to a disk, boot off of it and use it like that. Or use it in an Ubuntu Live Cd.
Whatever you want to do. Just google gparted and read a manual on it, takes just a bit not to
hard to use. Just stay focused on what you want to accomplish. But Windows usually is first in
line on drive because most all machines come with it pre-installed so anything to do with grub sounds a bit foolish using gparted. It is moving the Linux to the left on your partition scheme that takes the time, got to move all system over. Back-up your home folder just incase. Anytime you fool with your drive something has the possibillity of getting funky at any time.
If you read and understand what you are doing should go well!

---

### Post by Omnomnom on 2010-11-01
Thing is, I don't have a Vista disk.

---

### Post by bumanie on 2010-11-01
Vista and win7 have their own partition resizing tools for shrinking and expanding partitions. xp would only allow expanding. Right click on my computer, choose 'manage', then choose 'disk management' then right clicking on the vista partition you want to resize and it should be self explanatory from there-on. Then to change the linux partition, use gparted off a live cd or the specialised gparted live cd/usb from the gparted site. Windows will respond more favourably to be being resized with its own in-built tool.

---

