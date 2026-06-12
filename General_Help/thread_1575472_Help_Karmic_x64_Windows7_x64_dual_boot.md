---
title: "Help: Karmic x64 Windows7 x64 dual boot"
date: 2010-09-15
forum: General Help
---

### Post by ngrieb on 2010-09-15
My wife just got a new laptop: Toshiba A665 running Windows7 64, and wanted to dual boot. She didn't want to have to change any BIOS settings around or anything to switch from Win7 to Ubuntu, and I know that I need to do this for the Toshiba netbook I am on right now (a change to "Compatibility" mode or "AHCI" is needed when going from one to the other). So I tried to install Karmic x64 on her laptop. The grub2 boot loader got borked...so Win7 no longer opens...and the wireless card does not show up. Karmic boots slowly, and gives me an odd boot failure message really really quickly before loading grub2 I can't read it it is too fast. There are also some odd lags in the system on Karmic...like when typing on a terminal ans such...the letters will duplicate themselves as if they have been pressed a long time. As far as I know the specs are Intel Core i5 M450, 4 GB DDR3 RAM, 500 GB HD, nVidia GForce ?M. Can anyone help? Does anyone have this model working with Ubuntu?

I'm going to browse about for more solutions. Thanks in advance.

---

### Post by ngrieb on 2010-09-16
Ok, so I switched to 10.04 x64 and it worked much better...the initial screen resolution was much better and the wifi was detected. The error message before grub2 loading doesn't happen anymore, but there are still some flashes before the boot that I can't read...looks like a lot of hexadecimal numbers followed by something...when I next have the chance I will post the boot log file's output.

The thing I am attempting to find now is if there are any drivers for the nVidia GForce GT 330M. Does anyone know? Anyone have this working on this laptop?

The proprietary drivers look like they work, but then cause random freezes to happen durring use. I have seen posts for other laptops (Sony Vaio's mainly) but am not sure that these steps would work for the Toshiba.

---

