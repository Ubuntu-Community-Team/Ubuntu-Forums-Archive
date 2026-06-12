---
title: "wondering about Grub"
date: 2009-10-18
forum: General Help
---

### Post by Rainbowsix on 2009-10-18
I assume this is an easy answer, but I can't find it. Maybe I'm just a noob.

When I start my computer (which has only Ubuntu installed), Grub starts Ubuntu automatically. I'm pretty sure this is normal. My question is if I get a second hard drive and install another OS, is the Grub OS chooser menu going to show up automatically upon startup or is there something I have to configure?

---

### Post by mike555 on 2009-10-18
If you install another HD into your computer and install another Linux it will rewrite grub and include the first HD operating system .......... but if your talking about an external HD , you will want to be careful , because by default it will do the same thing , the problem is if you don't always have it plugged in your grub will error out looking for it when it's not plugged in .......... so if your talking about an external HD then you would want to install it's grub to the same partition as your installing to (not MBR),then use a different bootloader to boot (one that boots USB or whatever the external is)

---

### Post by Rainbowsix on 2009-10-18
Thank you, but what I was wondering about non-linux operating systems which don't use Grub by default.

---

### Post by mike555 on 2009-10-19
if your going to do a lot of "playing" with different operating systems (like I do) you might want a different bootloader , I use "GAG", but you must install grub or lilo to each partition you install Linux or bsd on (not mbr)because they each need a boot loader..... if your thinking Windows GAG will boot that just fine, except GAG doesn't boot USB drives,  in that case you should look for a bootloader that does, or use your BIOS settings.

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by P4man on 2009-10-19
> **Rainbowsix said:**
> I assume this is an easy answer, but I can't find it. Maybe I'm just a noob.

When I start my computer (which has only Ubuntu installed), Grub starts Ubuntu automatically. I'm pretty sure this is normal. My question is if I get a second hard drive and install another OS, is the Grub OS chooser menu going to show up automatically upon startup or is there something I have to configure?

Tricky question. 
Every disk has its own MBR and can have its own bootloader. So you could have grub on one disk and windows bootloader on another. And you can chainload from grub to boot the other drive, or select the bios boot menu (or change boot order) to boot one or the other drive first.

However not all OS's play nice with this. Windows will wipe whatever bootloader is on the first drive, even if you install windows on the second. So you better disconnect the first drive in this case so windows install its bootloader on its own drive

As for grub, if you run update-grub it will detect all other OSs in most cases.

---

