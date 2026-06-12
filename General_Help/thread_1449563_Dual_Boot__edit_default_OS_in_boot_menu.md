---
title: "Dual Boot : edit default OS in boot menu"
date: 2010-04-08
forum: General Help
---

### Post by mambo801 on 2010-04-08
hi guys

i would like to be able to edit which OS is set as default on the first selection menu.

i installed Ubuntu via windows xp. and have Grub 2 installed.

when i start my computer, first i see is the BIOS, then i have a menu which allows me to select either windows xp or Ubuntu (windows xp is the default which i'd like to change to Ubuntu). once i select Ubuntu, then i get the menu allowing me to select between the different upgrade versions.

from all the pages i read through on editing grub2 defaults, they only refer to the second menu that i get to pick between the upgrade versions or kernels (i think they are referred to).

What i'd like to do is set Ubuntu as the defualt on the first menu screen, as Ubuntu is my preferred OS and it can load automatically, then i don't care what the default upgrade version is loaded (this i have understood how to edit).

i hope i have described my problem, and any help will be appreciated.

cheers mambo801

---

### Post by darolu on 2010-04-08
The second menu part is confusing; I usually have all my kernels listed in the same menu the other OS's are.

Anyways, open Synaptic (*System > Administration > Synaptic*) and search for **startupmanager**, it will install a GUI that should help you, you can run it from *System > Administration > Startupmanager*.

---

### Post by oldfred on 2010-04-08
It sounds like you have wubi which boots Ubuntu thru the windows boot loader. Since you are using the Windows boot loader I do not know a way to change it.

Wubi is a good way for windows users to try Ubuntu as it is faster than a liveCD, allows updates and is a full install. But it is running with the windows boot loader and is inside the NTFS partition.

If you really like Ubuntu it may be time to convert to a full install in a separate partition(s). You will still be able to dual boot, I still use XP for one application.

---

### Post by mambo801 on 2010-04-14
> **oldfred said:**
> It sounds like you have wubi which boots Ubuntu thru the windows boot loader. Since you are using the Windows boot loader I do not know a way to change it.

Wubi is a good way for windows users to try Ubuntu as it is faster than a liveCD, allows updates and is a full install. But it is running with the windows boot loader and is inside the NTFS partition.

If you really like Ubuntu it may be time to convert to a full install in a separate partition(s). You will still be able to dual boot, I still use XP for one application.


Cheers thanks guys for the help and the hint,

I am a wubi user like you said, and i can now confirm that wubi Ubuntu users have the windows boot loader appears first. and hence you actually change the default OS in windows. and its very easy to do!!

here is a link to the wubi offical site and it goes straight to the change default OS instructions:

[https://wiki.ubuntu.com/WubiGuide#How do I make Ubuntu the default boot option?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?")

---

