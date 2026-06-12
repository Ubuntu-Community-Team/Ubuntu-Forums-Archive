---
title: "Installing Ubuntu... Well I wish I could.."
date: 2011-11-22
forum: General Help
---

### Post by karimruan on 2011-11-22
I have been without ubuntu since 10.10. I really miss it. I ended up buying some spare parts after my last ubuntu laptop died, and built a nice, compact little system. But here is the clincher, EVERYONE of my danged OS disks, be they Windows, Linux, FreeDOS or whatever is scratched as heck. They just wont boot. I am typing this on one of my generic Android tablets. So I need ubuntu, but have no means of burning an iso, creating a bootable thumbdrive nada. 

It is a saaaad life when you are kept away from the Buntu because you didn't take care of your Disks. Any ideas on how to get this to work? I have a rooted Android tablet if that matters, with a USB adapter that will let me use my external hard drive, and a terminal emulator.

Anyway to use a terminal emulator to convert an iso to img and create a bootable USB drive?

---

### Post by F.G. on 2011-11-22
i think it might be the dd command that your looking for, careful though you select the right drive.

dd if=/path/to/file.iso of=path/to/usb/sdb

nb. you want to use 'sda' or 'sdb' rather than 'sda1' or'sdb1' as sdb is the physical drive and sdb1 is the logical one.

---

### Post by dniMretsaM on 2011-11-22
You could always order a free install disk from Canonical. Or just borrow a computer from a friend or something.

---

### Post by Elfy on 2011-11-22
> **dniMretsaM said:**
> You could always order a free install disk from Canonical. ...
Shipit is closed now, 
[http://www.ubuntu.com/shipit](http://www.ubuntu.com/shipit)

If you don't know anyone who can do it for you, perhaps a library or try taking it to a local LUG or your loco if it is local to you.

---

### Post by F.G. on 2011-11-22
hope my post was helpful, on thing though make sure you have the right usb path, so you don't end up formatting something you want to keep.

---

### Post by asifnaz on 2011-11-22
Ask for some friend and family help or look for net cafe . I really take care of my CDs .

Somebody has stolen my PC (Debian 6) as well typing these lines from a windows 7 machine .

I am also missing ubuntu

---

### Post by dniMretsaM on 2011-11-22
> **forestpiskie said:**
> Shipit is closed now, 
[http://www.ubuntu.com/shipit](http://www.ubuntu.com/shipit)

If you don't know anyone who can do it for you, perhaps a library or try taking it to a local LUG or your loco if it is local to you.

Thanks for the correction.

---

### Post by philinux on 2011-11-22
Moved to General Help.

Would unetbootin help you.
 [http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

