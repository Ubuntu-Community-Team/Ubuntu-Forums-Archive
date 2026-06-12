---
title: "Dual boot with 2 drives:  Upgrading Windows slave?"
date: 2009-07-29
forum: General Help
---

### Post by Michl on 2009-07-29
On my work computer I dual boot with two drives with
Windows 2000 on the slave.  I would like to install 
Windows XP for the two programs I need to use in 
windows (taxes and CAD).

Can I do this without reinstalling Hardy?  Last time
I checked into this the answer was no, but maybe I
missed an option for doing this. 

If this helps:  I have a /home partition on the drive
with ubuntu.

Thanks!

---

### Post by michy99 on 2009-07-29
You should not have to re-install Hardy. That being said, it is always a good idea to back up any important data if you haven't done so already.

Do you want to install XP along side 2000 or replace 2000? If you are replacing 2000 with XP, are you doing an update or a completely new installation?

---

### Post by zarqoon on 2009-07-29
The main problem as I see it would be the windows install killing grub and therefore making hardy unable to boot. This should be fixable with an Ubuntu Live DVD. Search the forum for reinstall grub
On my system I have windows installed on a different drive and boot ubuntu and windows think they are on the main boot drive. 
I did this by removing the other drive prior to install. This way windows does not know ubuntu exists and vice versa.
Its not an ideal solution as i have to select what system i want to boot with the bios, but my board has a thingy where i can press f8 during post and select the device i want to boot from for one boot only.
Of course this will only work if the grub you are using is not already installed on the windows disk.
Physically removing the disk should not be required if you disable it in the bios settings but it is safer if you want to exclude any possible data loss.

---

### Post by Michl on 2009-07-31
> **zarqoon said:**
> The main problem as I see it would be the windows install killing grub and therefore making hardy unable to boot. This should be fixable with an Ubuntu Live DVD. Search the forum for reinstall grub

Thanks -- that was the problem.  I also remember that fixing
the grub was more c omplicated then.

[QUOTE=michy99]Do you want to install XP along side 2000 or replace 2000? If you are replacing 2000 with XP, are you doing an update or a completely new installation?[/QUOTE]

This got me thinking.  I don't want to do a clean install because
that hard drive contains a decade worth of material and old programs that won;t work in XP, I very rarely use, but would still like to have available as an option.  The upgrade won;t solve the out-of-date software problem and also, I can't upgrade from 2000 Professional to XP home.  I could try to install it in a separate folder, as suggested on the MS site.  Need to look into that.  Can I do that without worrying about ubuntu?

The other option is just to install XP on an old laptop for
the sole purpose of doing taxes once a year and the occasional
AUtoCad I need.  These are the only two programs that linux so far cannot replace.  (I have Qcad, but it is too weak and the Autocad I need does not run under wine.

Thanks again!

---

### Post by Michl on 2009-07-31
Just installed Windows XP to a folder in a partition that
has Windows 2000 on a laptop I use for experimenting.  Had
to fix the grub menu as mentioned above, but it's simple.

So my solution is to install Windows XP to the disk with
Windows 2000, leaving Windows 2000 intact, fix the grub,
and I have all I need.

THANKS!

---

