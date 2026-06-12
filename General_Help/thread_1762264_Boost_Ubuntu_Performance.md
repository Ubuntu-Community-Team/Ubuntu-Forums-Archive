---
title: "Boost Ubuntu Performance"
date: 2011-05-19
forum: General Help
---

### Post by kmccmk9 on 2011-05-19
Hello, is there any way to boost performance by adding memory sticks? Similar to the ability to do this in Windows 7?

---

### Post by noah++ on 2011-05-19
**Edit: **I think I misunderstood the question, so you should probably ignore this.

Yes, the same principles that make adding memory good for Windows performance also make it good for Linux performance. And no configuration is needed.

On the other hand, and as for those principles, it's not as if adding memory results in an automatic performance gain. It only helps if things were slow because you were running out of available memory.

---

### Post by chellrose on 2011-05-19
I believe so.  I was able to get Ubuntu running faster on my old dinosaur of a laptop by adding more RAM.  That was back in the days of Hardy, but I'd presume it still works for newer versions.

---

### Post by prshah on 2011-05-19
> **kmccmk9 said:**
> Hello, is there any way to boost performance by adding memory sticks? Similar to the ability to do this in Windows 7?

If you are thinking of Windows ReadyBoost, no, there is no way to do this. 

If you must, and if you have less RAM memory, you can THEORETICALLY setup a swap(file) on a USB stick and use that instead of your HDD. ReadyBoost does much the same thing. It stores cache on pen drive, freeing up system memory while reducing impact on cache; it DOES NOT increase the maximum memory to programs and services. Your system memory does not suddenly increase from 64gb to 72gb by adding an 8gb pen drive.

Please post back if you want to try this.

---

### Post by kmccmk9 on 2011-05-25
> **prshah said:**
> If you are thinking of Windows ReadyBoost, no, there is no way to do this. 

If you must, and if you have less RAM memory, you can THEORETICALLY setup a swap(file) on a USB stick and use that instead of your HDD. ReadyBoost does much the same thing. It stores cache on pen drive, freeing up system memory while reducing impact on cache; it DOES NOT increase the maximum memory to programs and services. Your system memory does not suddenly increase from 64gb to 72gb by adding an 8gb pen drive.

Please post back if you want to try this.

Ok so if I understand you right this will aid in creating "virtual" RAM. I need this because I have a computer that shouldn't be running a Minecraft server and is slowly killing itself. So what steps do I need to take to set this up properly?

---

### Post by LordNeo on 2011-05-25
First thing to try should be to add up more swap space. If that doesn't entirely cut it, then adding a usb thumbdrive and setting it as an additional swap space.

---

### Post by prshah on 2011-05-25
> **kmccmk9 said:**
> Ok so if I understand you right this will aid in creating "virtual" RAM. I have a computer that shouldn't be running a Minecraft server and is slowly killing itself. So what steps do I need to take to set this up properly?

No, it does not create "virtual" RAM. It only is an additional (fast) swap space.

> **LordNeo said:**
> First thing to try should be to add up more swap space. If that doesn't entirely cut it, then adding a usb thumbdrive and setting it as an additional swap space.

If this is a fixed requirement (and not a one-off) then, as suggested, it is better to create/increase swap space on your HDD, rather than your USB stick.

However, the USB stick will be faster. This is what you need to do:

```
# create a swap file, eg 1.5GB (2GB pendrive is only 1.7GB available)
sudo dd if=/dev/zero of=/media/pendrive/swap bs=1024 count=1572864
# "format" it as swap
sudo mkswap /media/pendrive/swap
# activate the swap and give it a higher priority than the current swap
sudo swapon -p 10 /media/pendrive/swap
# check if swapspace active and priority higher than default (-1)
swapon -s

```

Notes: Replace "/media/pendrive/" with the actual path to your pendrive. Please be very very very careful with the "dd" command, it can cause instantaneous damage to data if used wrongly.

Please post back if you run into problems, with details. If it works fine, and you want to make it permanent, please post back.

---

### Post by 3rdalbum on 2011-05-26
You get a lot more usable memory on Linux, due to two reasons:

1. Lower memory use overall (more efficient coding)
2. On 32-bit systems, Windows reserves up to 2 GiB of RAM for itself, most of which will never get used. Linux just reserves what it needs as it needs it, so you've got more usable RAM at most times.

Readyboost is really a hacky workaround for Windows' tendency to grab RAM for itself.

---

### Post by kmccmk9 on 2011-05-26
> **prshah said:**
> No, it does not create "virtual" RAM. It only is an additional (fast) swap space.



If this is a fixed requirement (and not a one-off) then, as suggested, it is better to create/increase swap space on your HDD, rather than your USB stick.

However, the USB stick will be faster. This is what you need to do:

```
# create a swap file, eg 1.5GB (2GB pendrive is only 1.7GB available)
sudo dd if=/dev/zero of=/media/pendrive/swap bs=1024 count=1572864
# "format" it as swap
sudo mkswap /media/pendrive/swap
# activate the swap and give it a higher priority than the current swap
sudo swapon -p 10 /media/pendrive/swap
# check if swapspace active and priority higher than default (-1)
swapon -s

```Notes: Replace "/media/pendrive/" with the actual path to your pendrive. Please be very very very careful with the "dd" command, it can cause instantaneous damage to data if used wrongly.

Please post back if you run into problems, with details. If it works fine, and you want to make it permanent, please post back.

Thanks, problem is I can't find the directory I checked both the media folder as well as the mnt folder and there was nothing inside.

---

### Post by kmccmk9 on 2011-05-27
How can I find the pen drive directory?

---

### Post by alem189 on 2011-05-27
> **kmccmk9 said:**
> How can I find the pen drive directory?

Go into the /media directory. There will be a folder in there, usually named after the company that made your pen drive.

---

### Post by kmccmk9 on 2011-05-27
> **alem189 said:**
> Go into the /media directory. There will be a folder in there, usually named after the company that made your pen drive.

Oddly there is only floppy and floppy0

---

