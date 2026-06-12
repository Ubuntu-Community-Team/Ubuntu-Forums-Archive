---
title: "grapevine, wine alternitive?"
date: 2009-08-22
forum: General Help
---

### Post by kooley on 2009-08-22
hey pplz i was wondering if ne one could help me, iv been trying to play windows games in my linux using wine and wine kinda dosent work well, so i was wondering about posible alternitives, i know of cedega but i dont have a credit card or purches a subscription, and i heard of a program called grapevine thats suposed to be good, and i was wondering how to getahold of this program, and how to install/use it.

---

### Post by bobince on 2009-08-22
Grapevine is a frontend GUI, not an alternative. There's no real ‘alternative’ to Wine; everything, including Cedega and Crossover, comes from the same original code; the differences are not huge.

---

### Post by P4man on 2009-08-22
cedega (or transgaming) is basically wine but preconfigured for a lot of apps. It uses the same code, its just more convenient to use.

Wine is no miracle solution for playing windows games. Fact is linux isn't better at running windows apps than windows. IT may or may not work, but its far from perfect. Best bet is checking your game on winehq website. If its not reported to run properly, dual boot is your only realistic option for playing that game.

---

### Post by Ms_Angel_D on 2009-08-22
Though they are the same thing as the above posters mentioned, sometimes you'll find it is easier to use the GUI's to get the proper setup for you game/program. 

I couldn't get guild wars to work in wine when I first started using Linux, but It set up perfectly using [Play On Linux]("http://www.playonlinux.com/en/").

So it might be worth while to look into some alternative ways to install the game/app.

---

### Post by 3rdalbum on 2009-08-22
> **Ms_Angel_D said:**
> I couldn't get guild wars to work in wine when I first started using Linux, but It set up perfectly using [Play On Linux]("http://www.playonlinux.com/en/").

+1 for Play On Linux.

---

### Post by kooley on 2009-08-24
thnx for the playonlinux idea i downloaded that and have been playing around with it but i keep getting a msg saying something about needing 3d acceleration. i was wondering how do i get and install that?

---

### Post by P4man on 2009-08-24
depends on your videocard, you may need to install (or enable) drivers.
Open a terminal and type

```
lspci
```

and copy paste the output here

---

### Post by kooley on 2009-08-24
> **P4man said:**
> depends on your videocard, you may need to install (or enable) drivers.
Open a terminal and type

```
lspci
```

and copy paste the output here
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
 ok this is what i got after i typed "lspci"

---

### Post by P4man on 2009-08-24
You got a TNT2 videocard.. thats kinda .. old.
Im not sure this will work, but you may try nvidia-glx-71 drivers. I cant promise your card will be supported, but if you feel like trying:

```
sudo apt-get install nvidia-glx-71
```

its entirely possible upon reboot, you wont be able to boot in to X. Should that happen, press control+alt+F1 to get to a terminal and type:

```
sudo nano /etc/X11/xorg.conf
```

locate the device section where it says "driver". 

```
Section "Device"
	Identifier	"something nvidia here I suppose"
	Driver		"[COLOR="DarkRed"]xxx[/COLOR]"
EndSection
```

that "xxx" will probably be "nv" or "nvidia". You can try both. If neither works, go back to the vesa driver by putting "vesa" in there.

to save your edits, control+x and then Y.
to start X after making those changes type

```
startx
``` (maybe sudo is needed, im not sure)

or reboot.

Good luck, but dont have too much hope.

---

### Post by kooley on 2009-08-24
ok thnx ill give it a shot

---

