---
title: "Display flickers during drag/drop and dropdown menus. Help?"
date: 2011-06-11
forum: General Help
---

### Post by winchendonsprings on 2011-06-11
[SIZE=2]I have this problem on two of my machines so I tend  to think it is common but I can't find any info. Might because I'm not  sure what keywords to use.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Anyway, after 11.04 update on one machine and a fresh install on  another every time I try to drag/drop an icon or simply click a menu the  display flickers.[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]A few things I noticed -[/SIZE]
  
[LIST]
[*][SIZE=2]the wallpaper does not flicker[/SIZE]
[*][SIZE=2]all windows flicker[/SIZE]
[*][SIZE=2]all desktop icons flicker[/SIZE]
[/LIST]
[SIZE=2]All windows, icons, everything besides the wallpaper flicker and disappear for 2-3 seconds.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]So any ideas?[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]Is it gdm? Is it compiz? Xorg related?
[/SIZE]

---

### Post by wildmanne39 on 2011-06-11
> **winchendonsprings said:**
> [SIZE=2]I have this problem on two of my machines so I tend  to think it is common but I can't find any info. Might because I'm not  sure what keywords to use.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]Anyway, after 11.04 update on one machine and a fresh install on  another every time I try to drag/drop an icon or simply click a menu the  display flickers.[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]A few things I noticed -[/SIZE]
  
[LIST]
[*][SIZE=2]the wallpaper does not flicker[/SIZE]
[*][SIZE=2]all windows flicker[/SIZE]
[*][SIZE=2]all desktop icons flicker[/SIZE]
[/LIST]
[SIZE=2]All windows, icons, everything besides the wallpaper flicker and disappear for 2-3 seconds.[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]So any ideas?[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2]Is it gdm? Is it compiz? Xorg related?
[/SIZE]Hi, have you changed any settings in compiz? what are your system specs? including video card.

---

### Post by winchendonsprings on 2011-06-12
I have tried different compiz settings a bit but currently[IMG]http://i.imgur.com/PpY2Z.png[/IMG]

[IMG]http://i.imgur.com/qyJ1Q.png[/IMG]

 ```

ry@ry-G62x:~$ compiz --version
Compiz 0.9.4.0

```

```
ry@ry-G62x:~$ sudo lspci |more
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controlle
r (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

ubuntu 11.04 64 bits
new HP g62x laptop (although I did have the same problem on another machine)

---

### Post by wildmanne39 on 2011-06-12
> **winchendonsprings said:**
> I have tried different compiz settings a bit but currently[IMG]http://i.imgur.com/PpY2Z.png[/IMG]

[IMG]http://i.imgur.com/qyJ1Q.png[/IMG]

 ```

ry@ry-G62x:~$ compiz --version
Compiz 0.9.4.0

```

```
ry@ry-G62x:~$ sudo lspci |more
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controlle
r (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

ubuntu 11.04 64 bits
new HP g62x laptop (although I did have the same problem on another machine)
Hi, log in using ubuntu classic with no effects and see if it still happens.

---

### Post by winchendonsprings on 2011-06-13
I always use ubuntu classic (no unity) and I switched to metacity for most of today and it hasn't happened once.

So looks like the issue is with compiz. I guess I could just go through ccsm checking and unchecking things to narrow it down, not what I want to do. 

Any ideas off the top of your head?  If it was openGL or some sort of compositing issue I'd probably be clueless

---

### Post by wildmanne39 on 2011-06-13
> **winchendonsprings said:**
> I always use ubuntu classic (no unity) and I switched to metacity for most of today and it hasn't happened once.

So looks like the issue is with compiz. I guess I could just go through ccsm checking and unchecking things to narrow it down, not what I want to do. 

Any ideas off the top of your head?  If it was openGL or some sort of compositing issue I'd probably be clueless
Hi, I meant ubuntu classic with no effects. That does not have compiz installed at all, I believe. I know for sure that if you log in to unity you can not disable the unity plugin in compiz that will break unity.

---

### Post by winchendonsprings on 2011-06-13
I don't understand. I am aware that Unity resides on my computer but I have never logged in using it. I use the classic gnome desktop (not Unity). 

Compiz as well as Metacity are installed. Both can be used on the Classic Ubuntu/Classic Gnome desktop.(not at  the same time, of course) using 
```

compiz --replace & 

```or  ```


metacity --replace &

```

---

### Post by wildmanne39 on 2011-06-13
> **winchendonsprings said:**
> I don't understand. I am aware that Unity resides on my computer but I have never logged in using it. I use the classic gnome desktop (not Unity). 

Compiz as well as Metacity are installed. Both can be used on the Classic Ubuntu/Classic Gnome desktop.(not at  the same time, of course) using 
```

compiz --replace & 

```or  ```


metacity --replace &

```Hi, unity is just called ubuntu on the log in screen, then you should have ubuntu classic and ubuntu classic with no effects.

---

### Post by winchendonsprings on 2011-06-13
Sorry, You are right. I just logged out to check the log in options.

Although logging in with Ubuntu classic w/ no effects does the same thing as metacity --replace & 

Anyway, back to the issue at hand, Yes, Ubuntu classic w/ no effects (metacity minus compositing) works.

Even Metacity w/ compositing seems to work, actually. Toggled via gconf-editor seen here
[IMG]http://i.imgur.com/cU3ng.png[/IMG]

---

### Post by wildmanne39 on 2011-06-13
Hi, thats good is sounds like a compiz issue, in natty compiz was updated, I found a site that tells you how to downgrade compiz if you are using ubuntu classic.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by winchendonsprings on 2011-06-13
@wildmanne39 Thanks for all your help. I actually saw this post the other day and didn't pay close enough attention. I don't think I'm going to fall back a ppa I don't know but it looks like by the comments this is the way to fix things.

---

### Post by wildmanne39 on 2011-06-13
> **winchendonsprings said:**
> @wildmanne39 Thanks for all your help. I actually saw this post the other day and didn't pay close enough attention. I don't think I'm going to fall back a ppa I don't know but it looks like by the comments this is the way to fix things.
Hi,your welcome. If you are satisfied would you please go to thread tools at the top of the page and mark this thread as solved.

---

