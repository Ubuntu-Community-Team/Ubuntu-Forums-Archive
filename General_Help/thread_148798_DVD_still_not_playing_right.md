---
title: "DVD still not playing right"
date: 2006-03-22
forum: General Help
---

### Post by matthewinuk on 2006-03-22
My dvds still play back choppily. As in it jumps. as in it plays about 3 seconds then stops for a second then repeats this tirade.

DMA is enabled

libdvdcss2 is installed.

help.


Also. How can I assign additional disk space to the partition i have made available to ubuntu for files???

---

### Post by JimS on 2006-03-23
...

matthewinuk

DVD playing requires quite a bit of RAM,
so turn everthing else off.
If that doesn't work, reboot.
I have had a similar problem after running Firefox.
Even if I shut FF down, I still can't get some programs
to work right unless I have rebooted.
You might rip your DVD files to HD and play from HD.
Maybe you need more RAM.  I have 512MB.
Maybe your DVD drive is crapping out, mine did slowly.

Good luck,

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,

---

### Post by damu on 2006-03-23
Make sure DMA is enabled for your actual DVD player. I had the same problem : DMA enabled for cd-om (automatically done with Automatix). Having a closer look at it happened that my DVD player is cd-rom1, not cd-rom. So I had to turn the DMA on for this one, and after that my DVD would run ok.

So first check the name of your DVD player. You can have a quick look at Places/Computer/Filesystem/Dev and lokk at the name of the cd-rom ...in my case I have cd-rom, cd-rom1 (which happened to be my DVD player, and cd-rw which is my cd writer).

Then to allow DMA, [follow this]("http://easylinux.info/wiki/Ubuntu#How_to_speed_up_CD.2FDVD-ROM")

---

