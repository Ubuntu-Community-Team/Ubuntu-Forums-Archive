---
title: "Wont boot"
date: 2010-06-07
forum: General Help
---

### Post by Jammyc on 2010-06-07
Hi all,

Very new to this, but I've installed Ubuntu 10.04 netbook edition last  night on my netbook from a live usb that I created. I partitioned the  drive so that I could boot xp should I wish to. Thing is, when I chose  to boot Ubuntu, all I get is a black screen with a blinking cursor in  the top left. Safe (Recovery?) mode doesnt work either. I get lines of  text that hang, see attatched. XP is  working fine. I've googled the crap out of it and havent found any  solutions, or perhaps I've blatently missed em!

Anyway, apologies for my newbieness. Thanks for reading/replying.

[IMG]http://omg.wthax.org/07062010134_2.jpg[/IMG]

---

### Post by arrange on 2010-06-07
Only did some googling, but have you seen this thread?
[http://www.uluga.ubuntuforums.org/showthread.php?p=9342582](http://www.uluga.ubuntuforums.org/showthread.php?p=9342582)

---

### Post by Jammyc on 2010-06-07
> **arrange said:**
> Only did some googling, but have you seen this thread?
[http://www.uluga.ubuntuforums.org/showthread.php?p=9342582](http://www.uluga.ubuntuforums.org/showthread.php?p=9342582)
Hi, cheers for replying.

Yeah, Id seen that before. I cant disable what is used for boot, only rearrange the order in which they do. BIOS is odd on this computer.

Anyway, since I last posted, I have flashed my BIOS and updated it. After this, Ubuntu loaded. I downloaded and installed updates and after clicking restart in the updates pannel, GRUB now shows 2 installs of Ubuntu, neither of which will boot. Both just give me the blinking cursor and same as above in recovery mode.

Im on an Acer Aspire One D250 model Netbook and I've updated my BIOS to V1.5. Is there a later version?

Does anyone have any idea what might be happening?

---

### Post by oldfred on 2010-06-07
When you boot from BIOS hold down shift key until menu comes up.

 Then press e and replace quiet splash with hpet=force nolapic and control x to boot. then you can make it permanent with the link arrange gave you.

---

