---
title: "How do I clean-install ubuntu 10.10 over top of 11.04"
date: 2011-09-06
forum: General Help
---

### Post by Xtensity on 2011-09-06
11.04 wont allow me to install 10.10 at all just by running wubi.exe within the ISO. 

Nor can I install it by using the start up disk creator on a USB drive, it gets a boot error.

Nor can I install it by burning it to a CD.. still gets a boot error.

When I try to install it just by running the wubi.exe within the ISO, it gets permission denied after the first screen where I set which drive to install it to.  :(. 

11.04 is giving me too many errors and I need to downgrade. I'd rather have it do a clean install also so it shouldn't be this difficult.

---

### Post by wildmanne39 on 2011-09-06
Hi, it sounds like you are running windows with ubuntu installed through wubi is that correct? if so you uninstall it just like any other windows program then reinstall 10.10.
Here is a link for installing and uninstalling wubi.
[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

Thank you

---

### Post by Frogs Hair on 2011-09-06
If you are currently using a Wubi installation of 11.04 , backup the files you want to keep . Remove Ubuntu from Programs & Features in Windows , run disc cleanup and defrag . Install Wubi 10.10 and if you have any problems removing Wubi see the guide . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Xtensity on 2011-09-06
Actually I had originally installed 11.04 by suggestion of a friend because I saw him using it and I loved it so much more. Then I ended up frying my windows 7  on accident from within 11.04 and out of 15 guides i've tried and several different recovery disc and methods/techniques I have been unable to reboot it. I can only access my data. I do not plan on going back to windows 7 anyways.

So the issue... How do I install 10.10 from within 11.04 since I no longer can access my Windows 7. I have Win XP installed to Oracle VM if that will be any aid.

TL;DR: I CAN NO LONGER ACCESS MY WINDOWS. I find it highly unlikely that it is impossible to install a second ubuntu, on top of, or separate from within another version of ubuntu. Out of all the things, how can this not be possible?

---

### Post by wildmanne39 on 2011-09-06
Hi, you  do not install 10.10 from within ubuntu, you back up your data and make the livecd boot first in the bios then ubuntu 10.10 will load and you can wipe the drive and install 10.10.
Thank you

---

### Post by Xtensity on 2011-09-06
> **wildmanne39 said:**
> Hi, you  do not install 10.10 from within ubuntu, you back up your data and make the livecd boot first in the bios then ubuntu 10.10 will load and you can wipe the drive and install 10.10.
Thank you

The live boot CD I made(I tried 3 different burns), all gave me errors. All 3 asking me if I want to boot into mode 1 or 2. Which I have no idea what that was about. I booted into mode 1, and the ubuntu loader came up with TONS of errors.

I am redownloading it, going to put it on a USB and try that since I suspect that the download version I use was messed up.

---

### Post by Frogs Hair on 2011-09-06
Downgrades are not possible and this is the the only thing I know of . I don't know weather this is up to date and works with current versions of Ubuntu . [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html) wildmanne39 has the bes suggestion .

---

### Post by wildmanne39 on 2011-09-06
Hi, it is best to use the torrent when you download it will make sure the files are not corrupt.
Thank you

---

### Post by Xtensity on 2011-09-06
> **Frogs Hair said:**
> Downgrades are not possible and this is the the only thing I know of . I don't know weather this is up to date and works with current versions of Ubuntu . [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html) wildmanne39 has the bes suggestion .

I don't really want to downgrade. I want to install it like I would any other operating system. With most other operating systems if the desired partition already has an OS on it then it will clean install. Downgrade in my mind is when it keeps all your current files. I do not care if they get wiped.

---

### Post by wildmanne39 on 2011-09-06
Hi, make sure you reformat and repartition your drive because if you don't it might install along side your current ubuntu and take up twice the hard drive space.
Thank you

---

### Post by Xtensity on 2011-09-06
So do I need to download a Win XP iso, and install it in a separate partition, then go onto that and wipe the ubuntu partition and install the new ubuntu onto that -.-?

I hope I don't have to do all that. Hopefully this newly downloaded version will boot from USB effectively.

---

### Post by wildmanne39 on 2011-09-06
Hi, no you can open gparted from the livecd by choosing try then delete the partitions and reformat them, or choose to create partitions manually after you choose the install process but that is probably harder here is a guide to help you.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Thank you

---

