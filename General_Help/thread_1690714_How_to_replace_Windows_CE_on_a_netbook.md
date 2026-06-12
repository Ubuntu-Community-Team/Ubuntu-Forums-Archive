---
title: "How to replace Windows CE on a netbook?"
date: 2011-02-18
forum: General Help
---

### Post by X-Windows on 2011-02-18
I recently acquired a netbook that came preloaded with Windows CE and runs too slow for primary use. Although its specs aren't the highest, it runs too slow for my tastes. I have a decent amount of experience installing distros on standard computers but absolutely no experience with netbooks.

 Specs:  CPU:   VIA 300Mhz
OS:   Windows CE  
Memory :  128MB RAM with 2GB Flash Memory 
 (low specs but it was free... I'm not complaining)

 I have two questions; what would be the best distro for this (i was looking at xubuntu and eeebuntu) and is installing a distro/uninstalling windows CE significantly different than on a laptop?

I'm hesitant to go all gung-ho on it as I don't have a plan B in case windows gets corrupted.  This is a netbook that will be used almost exclusively for internet access, an OS with just Firefox would work fine.

---

### Post by Habeouscorpus on 2011-02-18
i torched my Windows on a netbook too! I recommend 10.10 desktop edition for ubuntu. I run Xubuntu on here too, and it works like a charm. Great battery life! (For extra bonus points, you can use the latest released kernel for even MORE battery life... but it's a little rough right now.)

Do your homework. See what people are saying about your model of netbook. See if there are ugly bugs to battle.

First off, make a live usb disk. Clone your Windows partitions with Clonezilla, so you CAN have a backup plan. Then boot to a live disk and start playing with the files in the Examples folder on the desktop. This will tell you how things look. Try to connect to wireless, and do other things that you plan on doing. See how applications work. (Of course, these are all the things I did not do. Learn from this :D )

If things look good, go for it! You won't regret it! And it's just like a laptop install. After all, netbooks are usually just baby laptops.

---

### Post by williamts99 on 2011-02-18
You are not going to get any Ubuntu action on there.  Though if someone has ported it, you might be able to run Android on it.

---

### Post by kerry_s on 2011-02-18
> **X-Windows said:**
> I recently acquired a netbook that came preloaded with Windows CE and runs too slow for primary use. Although its specs aren't the highest, it runs too slow for my tastes. I have a decent amount of experience installing distros on standard computers but absolutely no experience with netbooks.

 Specs:  CPU:   VIA 300Mhz
OS:   Windows CE  
Memory :  128MB RAM with 2GB Flash Memory 
 (low specs but it was free... I'm not complaining)

 I have two questions; what would be the best distro for this (i was looking at xubuntu and eeebuntu) and is installing a distro/uninstalling windows CE significantly different than on a laptop?

I'm hesitant to go all gung-ho on it as I don't have a plan B in case windows gets corrupted.  This is a netbook that will be used almost exclusively for internet access, an OS with just Firefox would work fine.


no version of ubuntu will run on that.
those netbooks are usually flashed, you can't just install what ever you want.

---

### Post by X-Windows on 2011-02-18
> **kerry_s said:**
> no version of ubuntu will run on that.
those netbooks are usually flashed, you can't just install what ever you want.

This is what I am wondering about. Will things get complicated if the laptop uses flash memory instead of solid state or disc? I foresee a problem here...

Has anyone successfully done this?

The laptop is a ["NB 1304"]("http://www.cellhut.com/NB-1304-7-Inch-Display-Mini-Netbook-30429.html") no name toshiba thing. Looks like an excellent area for linux to shine.

---

### Post by kerry_s on 2011-02-18
> **X-Windows said:**
> This is what I am wondering about. Will things get complicated if the laptop uses flash memory instead of solid state or disc? I foresee a problem here...

Has anyone successfully done this?

The laptop is a ["NB 1304"]("http://www.cellhut.com/NB-1304-7-Inch-Display-Mini-Netbook-30429.html") no name toshiba thing. Looks like an excellent area for linux to shine.

i doubt linux would ever shine on that, just the 2.6 kernel alone will eat up most of the memory. then theres flashing the os on there, flashing is always dangerous & can brick that in a heart beat. i bet it requires the special wires hooked directly to the chip to flash.

just be happy with what you got, it's an mid device. :lolflag:

---

### Post by williamts99 on 2011-02-18
> **X-Windows said:**
> Will things get complicated if the laptop uses flash memory instead of solid state or disc?.

The fact of flash memory, solid state disk, or magnetic hard drive has 0% to do with it at all.

I know where you are coming from, I have a couple of devices that run WinCE and having them freeze up after a period of time and having to reboot sucks, but there isn't much that you can do.  I would love to throw linux on them all.  Hell even my new TV runs linux([http://www.samygo.tv/](http://www.samygo.tv/)).

Android has been ported to some of these pseudo-netbook netbooks, if it happens to have exactly the same internal hardware, you might be able to use that, and even then the chances are slim.

Your best chance is if they happen to sell that same one as an Android pseudo-netbook and you can get the flash from it.

---

### Post by Seq on 2011-02-18
> **X-Windows said:**
> I recently acquired a netbook that came preloaded with Windows CE and runs too slow for primary use. Although its specs aren't the highest, it runs too slow for my tastes. I have a decent amount of experience installing distros on standard computers but absolutely no experience with netbooks.

 Specs:  CPU:   VIA 300Mhz
OS:   Windows CE  
Memory :  128MB RAM with 2GB Flash Memory 
 (low specs but it was free... I'm not complaining)

Well you're lucky. It looks like an X86-based WinCE device rather than some weird arm platform, so there is hope it might actually be easy. First thing to do is to see what it has for boot options (USB, PXE, etc).

For comparison, I run Linux on a few Wyse 3150SE thin terminals that are very similar (AMD Geode instead of VIA processors). They also shipped with x86 WinCE, and have 128MB Ram, but only 32MB storage ;).

If you can boot off something (USB is ideal) you can try Live images of various distros before you take the plunge and dive in. You can also probably do a image of the WinCE disk.

---

### Post by Seq on 2011-02-18
> **Seq said:**
> If you can boot off something (USB is ideal
Looks like it also has an SD slot. That might be usable.

---

