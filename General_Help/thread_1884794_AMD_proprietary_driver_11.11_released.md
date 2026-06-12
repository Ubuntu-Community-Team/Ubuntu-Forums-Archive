---
title: "AMD proprietary driver 11.11 released"
date: 2011-11-22
forum: General Help
---

### Post by MestreLion on 2011-11-22
How "safe" it is to install this in Maverick?

This or any other 11.x Catalyst, since the one that ships with Maverick is quite old now.

From "go ahead, it is as easy and clean as a PPA" to "DONT, its harder than compliling 3.x kernel and gnome", where does Catalyst for Maverick stands?

---

### Post by cariboo on 2011-11-22
Moved to General Help, as this has nothing to do with Precise Pangolin.

---

### Post by gradinaruvasile on 2011-11-22
> **MestreLion said:**
> How "safe" it is to install this in Maverick?

This or any other 11.x Catalyst, since the one that ships with Maverick is quite old now.

From "go ahead, it is as easy and clean as a PPA" to "DONT, its harder than compliling 3.x kernel and gnome", where does Catalyst for Maverick stands?

All catalysts are very easy to install, even easier than the nvidia drivers because you can do it from the current X session. But you have to know what are you doing. The driver has an option to generate .debs but it didnt work for me.
But the installer script is very easy to use, only that you have to remove your previous driver prior to installation. And reinstall the driver if another kernel upgrade comes along. And not forget to do an "aticonfig --initial" before using it.
I installed it 2 times when i tested amd cards (i use nvidia otherwise) and had no issues with installing (this meant uninstalling the nvidia driver and installing the amd one then reinstalling the nvidia driver).
Now the above i did in Debian, but it should work just as well in Ubuntu.

---

### Post by KingYaba on 2011-11-22
> **gradinaruvasile said:**
> The driver has an option to generate .debs but it didnt work for me.

I never do the debs thing, either. I just punch in sudo sh in the terminal and let the installer do its thing. aticonfig --initial -f at the end.

---

### Post by Claus7 on 2011-12-14
Hello,

I had installed it on maverick, yet I was facing some glitches and returned back to 11.10. Now 11.12 is out, and I'm thinking to give it a try. On maverick that is!

The good thing about 11.11+ is that it has opencl implemented in the driver.

Regards!

---

