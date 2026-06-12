---
title: "Lucid alongwith Mint &amp; Windows XP"
date: 2010-05-18
forum: General Help
---

### Post by sunnyengineeer on 2010-05-18
Hello,
        I've Ubuntu 8.10 alongwith Windows XP..
Now I've got CDs of [COLOR=Red]Ubuntu 10.04 & Mint[/COLOR]...
[COLOR=Red]Can someone guide me how can I tripple boot into all 3 OSes...[/COLOR]([COLOR=RoyalBlue]10.04/mint/xp[/COLOR])
I know its crazy to have both ubuntu & mint...(both are almost same)..
But still i wnat to try as many OSes as I can in my summer vacations here in India...

Plz help me....

thnx
Sunny Sharma

---

### Post by dcstar on 2010-05-18
> **sunnyengineeer said:**
> Hello,
        I've Ubuntu 8.10 alongwith Windows XP..
Now I've got CDs of Ubuntu 10.04 & Mint...
Can someone guide me how can I tripple boot into all 3 OSes...(10.04/mint/xp)
I know its crazy to have both ubuntu & mint...(both are almost same)..
But still i wnat to try as many OSes as I can in my summer vacations here in India...


Install 10.04 last.

---

### Post by john newbuntu on 2010-05-18
This article gives you the outline of how this can be done:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Some general thoughts:
1. If you do not have partitions to install Lucid/Mint, you need to create it.  This might mean reducing your existing XP or Ibex partition.  Should you choose to reduce the XP partition, defragment it first in Windows and then reduce it using Gparted that comes with Lucid/Mint liveCD.  Always make backups of your partitions/data.
2. If you plan on keeping Lucid or Mint, then install Grub2, the bootloader that comes with Lucid/Mint on to the MBR.  This will override your existing bootloader.
3. If you plan on using Lucid/Mint only for short time testing, consider installing it in a virtual environment such as virtualbox or VMWare.  This way, you need not set up any partitions.  It all goes under your guest OS environment.  Or you could just try it from the liveCD.

---

### Post by sunnyengineeer on 2010-05-18
> Some general thoughts:
1. If you do not have partitions to install Lucid/Mint, you need to create it. This might mean reducing your existing XP or Ibex partition. Should you choose to reduce the XP partition, defragment it first in Windows and then reduce it using Gparted that comes with Lucid/Mint liveCD. Always make backups of your partitions/data.
2. If you plan on keeping Lucid or Mint, then install Grub2, the bootloader that comes with Lucid/Mint on to the MBR. This will override your existing bootloader.
3. If you plan on using Lucid/Mint only for short time testing, consider installing it in a virtual environment such as virtualbox or VMWare. This way, you need not set up any partitions. It all goes under your guest OS environment. Or you could just try it from the liveCD.

hello,
         I already have those partitons...will defragment those...
I'll installing on a permanent basis...So can u plz elaborate me..i.e what to do...when to install which OS...their orders...and any specific details...

That will be very usefull...& nice from u..

thnx
Sunny Sharma

---

### Post by theozzlives on 2010-05-18
> **sunnyengineeer said:**
> hello,
         I already have those partitons...will defragment those...
I'll installing on a permanent basis...So can u plz elaborate me..i.e what to do...when to install which OS...their orders...and any specific details...

That will be very usefull...& nice from u..

thnx
Sunny Sharma

What filesystems you using, you can only defragment Microsoft filesystems, but you can't install Linux on those.

---

### Post by oldfred on 2010-05-18
You just need to plan what system will be in the MBR and that system then controls booting.

Multiboot with multiple partitions and separate data:
[http://ubuntuforums.org/showthread.php?t=1443814](http://ubuntuforums.org/showthread.php?t=1443814)

This uses old grub and grub2 does not like to be installed in the PBR, but shows some of the planning required:
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by john newbuntu on 2010-05-18
Assuming Lucid to be your main system, you would then go with installing Mint(Helena I suppose) first and then install Lucid.  This way, with the default installations, you would have grub2 boot loader on the MBR.
As far as partitions go, for a real simple install, you need at least one root(/) partition per OS.  You could share the swap between all your linux installations.

---

### Post by sunnyengineeer on 2010-05-19
Hello,
           So nice to have those helping hands from so much people..
So Im almost clear in my mind....Finally I've decided to do like :-

1. Go to Windows Disk Mgmt...Erase Ubuntu partition of 8.10..
2.Fix MBR of Windows using its CD
3. Create partition from that,ehich was once used by 8.10
4. Install Mint....by creating ext3 filesysytem for it..& also cretaing a swap for it...
5. Now installing Ubuntu 10.04...Using a difft partition for it..but same SWAP...

WIll it work fine...any remarks or suggestions...
One more thing what shd be the order...
i.e Ubuntu after Mint or vice versa...

thnx
Sunny Sharma

---

### Post by oldfred on 2010-05-19
I like to use gparted for partition editing creating etc. It is on the liveCD or you can download it as a liveCD.

If you want Ubuntu to control the MBR then installing it last is slightly easier. You can always reinstall a boot loader to the MBR. Most, except windows, allow you to choose where to install the boot loader or choose not to install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

