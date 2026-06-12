---
title: "Cannot access windows 7 Partition"
date: 2010-06-27
forum: General Help
---

### Post by ricardino on 2010-06-27
Hi all, 

Ive just installed ubuntu on my laptop in a dual boot configuration, and its working perfectly. However, i am unable to access my windows partition from my ubuntu install. The drive shows up as a device named SYSTEM RESERVED, but i am still able see basic properties, such as its size. All im able to see on this drive when i access it via nautilus is a folder named boot and a folder names system volume information neither if which contain anything resembling my windows file system. I suspect that the problem may be caused my windows' new drive encryption although im not sure. Im just wondering if anyone else confirm my suspicions?

Thanks for any help

---

### Post by wilee-nilee on 2010-06-27
Is this a wubi install? and is the Windows encryption bitlocker?

---

### Post by ricardino on 2010-06-27
it is the wubi install, and i actually have no idea, because it was preinstalled when i bought it. If its bitlocker theres not much i can do is there?

---

### Post by wilee-nilee on 2010-06-27
> **ricardino said:**
> it is the wubi install, and i actually have no idea, because it was preinstalled when i bought it. If its bitlocker theres not much i can do is there?

I am not sure about bitlocker, but on a wubi I did a couple of days ago just for kicks I have no access to XP from it. I am a regular dual-booter, so the install was just to have some experience with it for helping others. 

I don't think the windows partition is accessible from a wubi, and if it is I would be surprised, as Ubuntu is just a file in the ntfs partition, I don't think it has anything to do with a encryption.

---

### Post by ricardino on 2010-06-27
Ahh i see, I think i might remove it and reinstall as a proper dual boot instead of a wubi then. Thanks for the help.

---

### Post by wilee-nilee on 2010-06-27
> **ricardino said:**
> Ahh i see, I think i might remove it and reinstall as a proper dual boot instead of a wubi then. Thanks for the help.

You might check with the live cd that you will be able to access Windows, and a dual boot will be better and more stable even if it can't access Windows, but I think it will from the live cd and a install.

---

### Post by bcbc on 2010-06-27
You can find your windows partition under the /host directory.

Still, install directly - never a bad idea.

---

### Post by wilee-nilee on 2010-06-27
> **bcbc said:**
> You can find your windows partition under the /host directory.

Still, install directly - never a bad idea.

I didn't see the XP partition in the wubi install I did, but I mainly did it to have a booscipt of it and just to understand how it works. Easy install runs about as fast as my thumb running a full install of Maverick.

---

### Post by wilee-nilee on 2010-06-27
Hey I found it in home side bar-file system-host. I looked in synaptic and the ntfs prog and 3 other associated were on.

---

### Post by gadolinio on 2010-06-28
> **bcbc said:**
> You can find your windows partition under the /host directory.

Still, install directly - never a bad idea.
+1.
I don't know how it works, but ubuntu can see the windows partition and shows it in /host, when installed with wubi. When installed in its own partition, it finds windows in /media/some_driver's_name.

You might want to test ubuntu for some time using the same wubi install you have now, and when you're sure that you feel comfortable with the OS, go for a full install.

---

### Post by shadow1983 on 2010-06-28
I found this problem as well, it turned out to be Wubi cant see the drive it is installed on accept for the space allocated. You can either do what other people have said and set up a duel boot system, Or as your running windows 7, go to the computer management and create a new partition. Then use Wubi and install it on the new partition you have created (fill up the whole space), this will allow you to see your Windows 7 Partition within ubuntu. While still having the ability to uninstall it as a windows program when needed.

---

### Post by wilee-nilee on 2010-06-28
> **shadow1983 said:**
> I found this problem as well, it turned out to be Wubi cant see the drive it is installed on accept for the space allocated. You can either do what other people have said and set up a duel boot system, Or as your running windows 7, go to the computer management and create a new partition. Then use Wubi and install it on the new partition you have created (fill up the whole space), this will allow you to see your Windows 7 Partition within ubuntu. While still having the ability to uninstall it as a windows program when needed.

Read the thread it is available in wubi.

---

### Post by shadow1983 on 2010-06-28
Yea read it wrong sorry, ignore my post

---

### Post by wilee-nilee on 2010-06-28
> **shadow1983 said:**
> Yea read it wrong sorry, ignore my post

I didn't even know it could be done myself until bcbc suggested the location, it is easy to miss stuff on threads.;)

---

### Post by Mark Phelps on 2010-06-28
> **ricardino said:**
> Hi all, 

Ive just installed ubuntu on my laptop in a dual boot configuration, and its working perfectly. However, i am unable to access my windows partition from my ubuntu install. The drive shows up as a device named SYSTEM RESERVED, but i am still able see basic properties, such as its size. All im able to see on this drive when i access it via nautilus is a folder named boot and a folder names system volume information neither if which contain anything resembling my windows file system. 
In preinstalled Win7 systems, the partition you're mentioning is typically the one containing the boot loader files.  If this is indeed the case on your machine, LEAVE IT ALONE!!  You mess with this, and you won't be able to boot Win7 anymore.

> I suspect that the problem may be caused my windows' new drive encryption although im not sure. Im just wondering if anyone else confirm my suspicions?

This two-partition scheme, in which the boot partition is NOT encrypted, but the OS partition IS, was the primary reason that MS came up with their two-partition default install scheme for Win7.

Given that the OS partition is encrypted, you won't be able to see its contents.  IF you could see them, then simply booting from an Ubuntu LiveCD would bypass the encryption -- and that wouldn't be very secure, now would it?

---

