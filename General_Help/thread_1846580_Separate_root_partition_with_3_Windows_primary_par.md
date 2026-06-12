---
title: "Separate root partition with 3 Windows primary partitions"
date: 2011-09-19
forum: General Help
---

### Post by Veren on 2011-09-19
Hello there,
I have installed Ubuntu and a bunch of other distros a couple of times now, but I've been wondering about this: I have been dual-booting with Windows 7 for gaming purposes, and I have 3 W7 partitions: 1) 100MB bootloader or whatever it is, it creates itself during installation, 2) about 25GB /C: and 3) about 100GB /D:. That makes 3 primary partitions total. Then, I do Ubuntu installation and I want to have a separate /. However, when I create / of any size, I can no longer create any partitions for /home or /boot, even though they would be extended, and I have free space. In distributions like Chakra, I can use a partitioning tool that creates an extended partition that covers the entire remaining space after a W7 installation, and then create my Linux partitions on it. What can be done in Ubuntu ? I tried creating my / as extended, but it then assings it some number other than /dev/sda4. I am not good at these things, I've done some research but I couldn't come up with anything, sorry.
Thanks for any advice

---

### Post by cryptotheslow on 2011-09-19
It sounds like you are on the right track.

You create an extended partition which will be sda4, and then you create logical partitions within it for /  /home  swap    etc.  The logical partitions within the extended will be sda5, sda6 etc. That is perfectly fine.

---

### Post by Bucky Ball on 2011-09-19
> **cryptotheslow said:**
> It sounds like you are on the right track.

You create an extended partition which will be sda4, and then you create logical partitions within it for /  /home  swap    etc.  The logical partitions within the extended will be sda5, sda6 etc. That is perfectly fine.

+1. Four primary partitions is max. Three and an extended is considered as max but you can (theoretically) put however many logical partitions inside that extended partition as your machine can handle.

---

### Post by Veren on 2011-09-19
Thank you, I just don't know how to create logical partitions "on" the "big" extended partition, which I create after my W7 setup.

---

### Post by Bodsda on 2011-09-19
> **Veren said:**
> Thank you, I just don't know how to create logical partitions "on" the "big" extended partition, which I create after my W7 setup.

Use a program called 'gparted' on Ubuntu to create the extended and logical partitions. It is a very nice graphical partition editor. You just select the empty space and create the desired partition from the menu. 

Hope this helps,
Bodsda

---

### Post by ppv on 2011-09-19
Once you have created the extended partition you should be able to create logical partitions in it from Ubuntu itself, maybe by using a live CD. Or probably you can do so when installing Ubuntu where you select the partition to install Ubuntu on.

---

### Post by Veren on 2011-09-19
> **Bodsda said:**
> Use a program called 'gparted' on Ubuntu to create the extended and logical partitions. It is a very nice graphical partition editor. You just select the empty space and create the desired partition from the menu. 

Hope this helps,
Bodsda

Thank you, I completely forgot that the liveCD comes with gparted ! :P I can play with that.

---

### Post by Bucky Ball on 2011-09-19
You can, but if you want to create a /home and other Linux EXT* logical partitions in the extended one you are better doing that when you do the install. Go for manual partitioning when you get to that bit and set up your extended and logical partitions there (you can install /, /home, and /swap inside the extended if you like; Ubuntu doesn't need to be on a primary partition, unlike Win).

---

