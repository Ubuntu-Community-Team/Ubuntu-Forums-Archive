---
title: "Need help switching from Vista to Linux"
date: 2009-11-26
forum: General Help
---

### Post by wbreslin951 on 2009-11-26
Hey guys, I'm gonna try to make this as straight forward as possible. I have alot that I need answered, so here goes nothing.

I'm switching to Linux from vista, quite honestly, vista pisses me off because its extremely buggy and too unreliable. In fact, my computer just stopped even booting, and the only reason I'm on here is that I have already dual booted my comp with linux. Thank god i can get access to all my files still =].

T.G.F.L (Thank god for linux =])

Anyways, here's a list of things that I NEED my linux box to do

-Internet Connection Sharing (wireless internet connection shared to wired connection)

-Music (listening, editing, etc.)

-Flash Viewing/composition

-Photo editing

-Web page design/graphic design

-Gaming (the likes of counter strike, call of duty, etc)

-Video Editing (HD, heavy on the hardware, i know)

-Webcam (not really, but it'd be nice lol)

Anyways, I've solved a few of these problems already, I've got Audacity for music recording, GIMP for photo editing, possibly Wine for Gaming, but i'm not sure how well it will run. I'm really looking forward to your guys' help on this. Thanks! PS i'm about to DL and install 9.10 so =]]

Oh, and in case it helps any, here's what sysinfo says about my computer =]:

Compaq Presario CQ60

_CPU_

2.16 GHz processor, L2 Cache 1024 KB
2 Gigs Ram
Integrated Graphics
Realtek RTL8101E/RTL8102E PCI Express Network card (i believe its made by atheros? im not sure, having problems setting up wireless though, definately need help with that. Thanks!)

Take it easy guys

---

### Post by Yvan300 on 2009-11-26
Well for your webcam you can use cheese, which is found in the repos.

Openshot for video editing, which is also found in the repos.

Don't really understand what your mean by flash composition.

---

### Post by acoc on 2009-11-26
> Internet Connection Sharing (wireless internet connection shared to wired connection)

I haven't found any good graphical way to do this, but via the command line it can be done: [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

> -Music (listening, editing, etc.)

Listening - [COLOR="Red"]Banshee[/COLOR] , Editing - [COLOR="Red"]Audacity[/COLOR]

> -Flash Viewing/composition

Viewing - [COLOR="Red"]Firefox[/COLOR] with [COLOR="Red"]flash-installer[/COLOR], Composition - I think you're out of luck on that one

> -Photo editing

[COLOR="Red"]Gimp[/COLOR] is the most powerful.  Photoshop is available through crossover office

> -Web page design/graphic design

Webpage design - [COLOR="Red"]drupal[/COLOR], I've never needed anything else. There is [COLOR="Red"]inkscape[/COLOR] and [COLOR="Red"]blender[/COLOR] for graphic design, but I don't have a lot of experience with either.

> -Video Editing (HD, heavy on the hardware, i know)

[COLOR="Red"]kdenlive[/COLOR], but again I don't have a lot of experience with it

> -Gaming (the likes of counter strike, call of duty, etc)

I would say you could use wine/crossover office or games/or cedega, but if you've got a windows license, dual boot.  This is the only way you will remain happy regarding games.

> -Webcam (not really, but it'd be nice lol)

No clue, never owned one.

Hope this helps,

John

---

### Post by Bruce H on 2009-11-26
[Swish Max]("http://www.swishzone.com/index.php") is a flash authoring tool that runs well in Wine. I don't know how good it really is, and it's proprietary, and costs $150.00 US. Still, it's a lot cheaper than Flash from Adobe.

However, I was able to install and run the demo just fine in Wine.

---

### Post by wbreslin951 on 2009-11-27
I've heard good things about swish max, and being an open source lover, i have no problem torrenting it =].

Quick question, if i downloaded a torrent that had an embedded virus, ran the program under wine, could it screw up wine and cause me to have to reinstall it?

and also regarding gaming, i've just gotten to a point where there's no way i can boot into vista, looks like im gonna back everything up into linux and run the recovery partition, make vista really tiny so most of my disk space is just linux, and use it for strictly gaming lol. i really hate vista. i mean, really. really. hate vista.

---

### Post by audiomick on 2009-11-27
You need Ubuntu Studio
[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by wbreslin951 on 2009-11-27
wow ubuntu studio looks pretty friggin awesome! thanks for all the help guys, i appreciate the support!

still need help setting up wine ;) lol

not a complete n00b but pretty close lol
im learning python as we speak. seems pretty easy and awesome!


oh yeah one more thing. i have absolutely no wireless support for some reason, and i NEED it. I'm not sure what kind of wireless card i have but here's my lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

here's lspci -nn:

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

i believe thats my wireless card and ethernet card, are they integrated? anyways thanks for all the support once again

---

### Post by acoc on 2009-11-27
Try the advice at [http://ubuntuforums.org/showthread.php?t=1320186&highlight=RTL8101E](http://ubuntuforums.org/showthread.php?t=1320186&highlight=RTL8101E) .  I think that's the same card.

John

---

### Post by wbreslin951 on 2009-11-27
i don't have the same card. i just remembered, i have an atheros wireless card. the realtek is my LAN card. for some reason my wireless card is almost completely invisible to ubuntu. the only thing that shows is Unknown Interface (pan0) in my network tools devices tab

---

### Post by acoc on 2009-11-27
It looks like they've fixed this in lucid (next release) and backported it to karmic.  Try the following:

```
sudo nano /etc/apt/sources.list
```

Then add the following line to the end of the file:

```
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted
```

Save

```
sudo apt-get update
sudo apt-get install linux-backports-modules-karmic
```

Restart and see if it works.

John

---

### Post by wbreslin951 on 2009-11-27
figured out what kind of wireless card i have:

Atheros AR5007 802.11b/g WiFi Adapter

Windows vista uses the athr.sys driver

i installed the madwifi drivers and it worked, 

but then i rebooted and now i can't get it to connect for the life of me. a dialogue keeps popping up asking for the WPA key, even though i know i entered it correctly before. any helP?

---

