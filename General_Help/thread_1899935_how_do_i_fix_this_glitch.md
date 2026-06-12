---
title: "how do i fix this glitch"
date: 2011-12-24
forum: General Help
---

### Post by cheeto_monkey on 2011-12-24
it keeps on doing this everytime i try to install it on my laptop [ATTACH]209683[/ATTACH]

---

### Post by 2F4U on 2011-12-24
And how are we supposed to know what exactly you are doing? Sorry, but my crystal ball is currently in repair.

---

### Post by John Peschken on 2011-12-24
> **2F4U said:**
> And how are we supposed to know what exactly you are doing? Sorry, but my crystal ball is currently in repair.

He's trying to install Ubuntu (like he said) and the screen looks like that.  No need to be rude.

---

### Post by QIII on 2011-12-24
Would it be possible for you to provide us with the make and model of the laptop and some of its hardware specs?

Also, did you check the md5sum of the image you downloaded and again of the image you burned to your optical media?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by West201 on 2011-12-25
As mentioned above please provide more info regarding your hardware, you should also the "check media" option before installing.

---

### Post by ofnuts on 2011-12-25
> **cheeto_monkey said:**
> it keeps on doing this everytime i try to install it on my laptop [ATTACH]209683[/ATTACH]I notice there still an "Appearance" windows title. Does this happen before you interact with that window or after you changed something with it? Looks like some unsupported video mode to me...

---

### Post by cheeto_monkey on 2011-12-26
the laptop specs are:

Graphics card: ATI Radeon X1270
Cpu: AMD Athlon(tm) Processor L110
the laptop model number is lt3113 and the manufacture is gateway 
anything else you need to know about the computer?

and it wasn't the appearance window it did that even when i logged in

---

### Post by West201 on 2011-12-26
> **cheeto_monkey said:**
> the laptop specs are:

Graphics card: ATI Radeon X1270
Cpu: AMD Athlon(tm) Processor L110
the laptop model number is lt3113 and the manufacture is gateway 
anything else you need to know about the computer?

and it wasn't the appearance window it did that even when i logged in

We have a very similar video card. When I used the propertiary drivers from ATI, I started to have graphical problems as well. I believe it's an issue with Gnome 3. Have you tried using Ubuntu without the " video propertiary drivers" ?

---

### Post by West201 on 2011-12-26
I fogot to ask which version of Ubuntu are you using ?

---

### Post by cheeto_monkey on 2011-12-26
I am using ubuntu 11.10
and i used the windows installer too so i don't know what would be wrong?

---

### Post by West201 on 2011-12-26
It must be Gnome 3, I had the same issue when I installed the ATI drivers. I would use classic mode if you want to keep your ATI drivers.

---

### Post by QIII on 2011-12-26
Did this start after you installed the latest ATI driver, or did this start happening immediately after you installed?

The ATI Radeon X1270 is no longer supported by the AMD/ATI drivers.  It is what they are now calling a "legacy" card.  To use a proprietary driver, you will need to install the legacy driver from the AMD website.

Since that is fraught with danger, I would suggest that you simply use the open source driver that comes with Ubuntu.  You may have fewer features that you can adjust, but it will be stable.

---

### Post by cheeto_monkey on 2011-12-27
I don't even know if it have the ati drivers installed in fact i just installed it so i don't know what drivers it put cause its impossible to read threw the glitch

---

### Post by cheeto_monkey on 2011-12-27
I also have a new problem now, i have windows 8 developer preview and its a new boot loader but grub didn't install and now it doesn't detect ubuntu so there's no option to select it. I also don't know how to install grub boot loader so what do I do?

---

### Post by West201 on 2011-12-27
> **cheeto_monkey said:**
> I also have a new problem now, i have windows 8 developer preview and its a new boot loader but grub didn't install and now it doesn't detect ubuntu so there's no option to select it. I also don't know how to install grub boot loader so what do I do?

Does the glitch also happen in a "classic desktop" ? 
Are you running in a special desktop effects ?

---

