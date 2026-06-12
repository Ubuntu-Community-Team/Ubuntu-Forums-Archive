---
title: "How to boot Ubuntu &quot;automatically&quot; (without GRUB)?"
date: 2010-05-18
forum: General Help
---

### Post by petike on 2010-05-18
Hello,
I would like to have "only one" operating system to be installed, and that's "Ubuntu".
So as I have only one operating system installed, I "don't need" the GRUB boot-loader to appear at the computer start to choose an appropriate operating system.

I want to achieve something similar as when I had only Windows - after the computer start, Windows started automatically - so I want the same with Ubuntu - **"after the computer start, Ubuntu should boot automatically"** - is this possible?


[I]P.S.:
Of course, when the Linux kernel is updated, I want "that new kernel" to boot.

P.S.2:
I think, that automatic start of Ubuntu (without launching GRUB) will be faster, am I right?
[/I]

---

### Post by vinan on 2010-05-18
[COLOR=black][FONT=Verdana]How did you install ubuntu??[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Are there any other OS. Installed in the system before you installed Ubuntu.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Other wise it should be default, ubuntu boot up without the Grub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I usually do it like this,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]During the instalments[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]in the choose edit partition menu,  delete all partitions and make a swap 1½ time,  ram size[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]and a ext4 file partitions around 50gb, and rest as also ext4 to storage,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]                                                               [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]but there shold be a way to edit the GRUB menu to just boot on Ubuntu,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]buy the way[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Welcome to world without fences and walls [/FONT][/COLOR]

---

### Post by Jakiejake on 2010-05-18
Had the same problem with Linux Mint
Ended up re-installing it
It won't improve the boot time much but it will because you don't have to load the GRUB
Try removing the GRUB folder
How? Google is your friend.

---

### Post by Jakiejake on 2010-05-18
Oh P.S. Try Start-Up manager

---

### Post by Grenage on 2010-05-18
On Grub2, you can change the timeout; you can make it 1 second or the like:

```
gksu gedit /etc/default/grub
```

The default looks like:

```
GRUB_TIMEOUT=10
```

Then update grub:

```
sudo update-grub
```

It's possible that you could set the timeout to be 0 and it would 'insta-load' Ubuntu, but it might sit there forever - I've never changed it.

> P.S.:
Of course, when the Linux kernel is updated, I want "that new kernel" to boot.

It will.

> P.S.2:
I think, that automatic start of Ubuntu (without launching GRUB) will be faster, am I right?

Grub will always be there, there has to be a bootloader (even Windows has one).  It's just a question of whether you see it or not.

---

### Post by CharlesA on 2010-05-18
Grenage hit it on the head.

You shouldn't remove GRUB since that's what Ubuntu uses to load, just change the timeout to a lower value (or 0 to hide the menu by default)

---

### Post by petike on 2010-05-18
Thanks for the answers,
and I have one more question about "partitioning" the hard-disc.

I know **"how many and which"** partitions I want to have (I have an 80-GB hard-disc):
=====================================
- **"/" (root)** partition - 40 GB (I am planning to run Windows on VirtualBox there, therefore so much space)
- **"linux-swap"** partition - 2 GB
- **"/boot"** partition - 200 MB
-** "/data" **- the rest
=====================================
, but I don't know **"how to order"** them to achieve the "best performance" (if it depends, maybe if the "/boot" partition was the first one, the startup would be faster, but I really don't know).

So for example, is this order a "good one": 
=====================================
-1.) **"/" (root)**
-2.) **"/data"**
-3.) **"linux-swap"**
-4.) **"/boot"**
=====================================
?

*P.S.: I don't need to have a separate "/home" partition because all my data are stored on the "/data" partition.*

---

### Post by CharlesA on 2010-05-18
Normally you don't need a seperate /boot partition unless you have an older BIOS that isn't able to see the large partitions.

If your BIOS is one of those, I believe it expects the /boot partitions to be at the 'front' of the drive (on top)

All my installs have only two partitions: "/" and swap.

---

### Post by pmlxuser on 2010-05-18
doesn't really matter... it on the same disk anyway....

---

### Post by pmlxuser on 2010-05-18
> **CharlesA said:**
> Normally you don't need a seperate /boot partition unless you have an older BIOS that isn't able to see the large partitions.

If your BIOS is one of those, I believe it expects the /boot partitions to be at the 'front' of the drive (on top)

All my installs have only two partitions: "/" and swap.

indeed only problem if system fails you loose all data if you do a clean install, while if you have a separate data or /home partition the risk is less...

---

### Post by CharlesA on 2010-05-18
> **pmlxuser said:**
> indeed only problem if system fails you loose all data if you do a clean install, while if you have a separate data or /home partition the risk is less...

True. In my case, all important data is stored on a separate device which Ubuntu doesn't have native drivers for (and which already has a file system on it).

---

### Post by Jakiejake on 2010-06-02
Solved?:confused:

---

