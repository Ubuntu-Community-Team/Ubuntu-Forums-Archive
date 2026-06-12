---
title: "UPDATE-GRUB is hanging, preventing kernel and other upgrades"
date: 2010-06-03
forum: General Help
---

### Post by utkjamie on 2010-06-03
I have some pending upgrades, one of which includes kernel 2.6.32-22 but whenever the upgrade gets to running the update-grub command, it gets stuck on "Found memtest86+..."

Here's the actual output...

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /memtest86+.bin

```

It's been hanging like this for hours today, preventing me from getting any of the pending upgrades. I've cancelled it several times, deleted the dpkg lock files and tried it again only to have it hang all over again.

How do I fix this problem?

---

### Post by utkjamie on 2010-06-04
No one else in all of Ubuntuland has run into this problem or has a possible solution?

---

### Post by philinux on 2010-06-04
It could be hanging trying to find an external drive that it knows about but is not plugged in. Not sure.

---

### Post by xolot1 on 2010-06-04
Are you sure that it is hanging? I thought I had this problem, then I realized that sometimes this step can take a long time. If you have the time, leave it for a while, and see if it completes. 

Also, you can check to see that grub is still doing something. I used **htop** to verify that processes that grub-update spawned were using the CPU, and this reassured me that progress was being made.

I think what is going on at this stage is that grub is scanning all your disks looking for various operating systems. Since hard disk accesses can be slow, especially many of them, the process may take longer than you expect (esp. if you have a fast processor/lots of memory).

edit:
I just went back to check this on my machine. 
I dual boot, yet this step took nearly two minutes on my quad core box fully idle.
If you have more OSes installed, or perhaps various kernel versions installed, you can see how this process might take even longer. 
So I recommend patience unless you're facing 20+ minutes of waiting.

---

### Post by Leppie on 2010-06-04
could you post the output of the boot info script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by philinux on 2010-06-04
> **xolot1 said:**
> Are you sure that it is hanging? I thought I had this problem, then I realized that sometimes this step can take a long time. If you have the time, leave it for a while, and see if it completes. 

Also, you can check to see that grub is still doing something. I used **htop** to verify that processes that grub-update spawned were using the CPU, and this reassured me that progress was being made.

I think what is going on at this stage is that grub is scanning all your disks looking for various operating systems. Since hard disk accesses can be slow, especially many of them, the process may take longer than you expect (esp. if you have a fast processor/lots of memory).

It should only take a couple of mins not **hours **like the OP said.

---

### Post by utkjamie on 2010-06-04
> **Leppie said:**
> could you post the output of the boot info script: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I'm thinking this may be a bad sign, but the boot info script appears to be hanging, too. It's been going for I'd guess about 20 minutes now.

As for checking the grub processes via htop, I can see about 27 different grub processes but each of them shows 0 on CPU%, MEM% and TIME+.

---

### Post by Leppie on 2010-06-05
> **utkjamie said:**
> I'm thinking this may be a bad sign, but the boot info script appears to be hanging, too. It's been going for I'd guess about 20 minutes now.
yes, normally it should take not more than a couple of minutes to complete.
try to completely remove grub and grub2:
```
sudo apt-get purge grub grub-pc grub-common
```then reinstall grub2:
```
sudo apt-get install grub-pc grub-common
```

---

### Post by Barafu Albino Cheetah on 2010-06-05
First of all, try installing bootloader to another place. USB flash or floppie would fit well, but Lynx has known problems with floppies.. 
Where are you installing grub? To MBR? Try removing other disk hardware and USB sticks. 
To the partition? Filecheck it thoroughly, use ext2 on it. 
If I remember it right, update-grub first constructs a configuration file, than uses grub-install to install it. Try calling grub-install directly. Does this work?

---

### Post by utkjamie on 2010-06-05
I think I figured it out. I was so distracted with work-related things yesterday, it never occurred to me to do something as simple as run dmesg. I noticed something screwy with an sdb1 device. I had completely forgotten that I had a 1gb microSD card plugged into my laptop (which has been quirky at other times). I removed that, ran the updates, and everything seems to have completed.

Apparently the grub configuration was trying to make sense of the microSD card and it just wasn't happening.

I'll report back if I have any further related problems with it, but I think this may have been the culprit.

I **really** appreciate the help and time you put into helping me figure this out!

---

