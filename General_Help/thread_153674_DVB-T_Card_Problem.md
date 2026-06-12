---
title: "DVB-T Card Problem"
date: 2006-04-01
forum: General Help
---

### Post by RoboJ1M on 2006-04-01
Hi,

I don't think my DVB-T PCI tuner card is working.
But I'm not sure, does anybody know of a HOWTO?

The card is a TwinHan Ter VP-3021 (bt878A and nxt6000 chips on the card)

I also have an old old Hauppauge analogue tuner in there too.

There are errors (I think) in my dmesg.
```

[4294696.475000] Linux video capture interface: v1.00
[4294696.541000] bttv: Unknown symbol tveeprom_read
[4294696.542000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294696.633000] bttv: Unknown symbol tveeprom_read
[4294696.634000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294696.644000] bt878: Unknown symbol bttv_read_gpio
[4294696.644000] bt878: Unknown symbol bttv_write_gpio
[4294696.644000] bt878: Unknown symbol bttv_gpio_enable
[4294696.722000] bttv: Unknown symbol tveeprom_read
[4294696.723000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294696.795000] ACPI: PCI Interrupt 0000:02:03.1[A] -> GSI 23 (level, low) -> IRQ 23
[4294697.055000] bttv: Unknown symbol tveeprom_read
[4294697.055000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294697.056000] bt878: Unknown symbol bttv_read_gpio
[4294697.056000] bt878: Unknown symbol bttv_write_gpio
[4294697.056000] bt878: Unknown symbol bttv_gpio_enable

```
I think thats the relevant part.

I'm unsure as to the installation process I should be following.

Thanks,

J1M.

---

### Post by RoboJ1M on 2006-04-01
Just in case, I removed the old analogue card.
No different, just less errors.

```

[4294697.142000] Linux video capture interface: v1.00
[4294697.208000] bttv: Unknown symbol tveeprom_read
[4294697.208000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294697.300000] bttv: Unknown symbol tveeprom_read
[4294697.300000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4294697.311000] bt878: Unknown symbol bttv_read_gpio
[4294697.311000] bt878: Unknown symbol bttv_write_gpio
[4294697.311000] bt878: Unknown symbol bttv_gpio_enable

```

---

### Post by RoboJ1M on 2006-04-02
OK, I fixed one problem through random poking of the modprobe command.

Turns out that a module called tveeprom.ko was names tveeprom.ko.HIDE.

I copied it to tveeprom.ko, rebooted and I get this in dmesg
```

[4294695.732000] Linux video capture interface: v1.00
[4294695.820000] bttv: driver version 0.9.15 loaded
[4294695.820000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294695.824000] bttv: Bt8xx card found (0).
[4294695.824000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294695.824000] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 20, latency: 32, mmio: 0xd8001000
[4294695.824000] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[4294695.824000] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[4294695.824000] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[4294695.838000] bttv0: using tuner=4
[4294695.863000] bttv0: add subdevice "dvb0"
[4294695.972000] bt878: AUDIO driver version 0.0.0 loaded
[4294695.976000] bt878: Bt878 AUDIO function found (0).
[4294695.976000] ACPI: PCI Interrupt 0000:02:02.1[A] -> GSI 20 (level, low) -> IRQ 20
[4294695.976000] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 20, latency: 32, memory: 0xd8002000
[4294696.088000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 21

```
But I still cannot use the "scan" command.
```

james@HAL:~$ scan uk-CrystalPalace
scanning uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```
And that's because there is no /dev/dvb folder.

There were /dvb/adaptor<0-3>/frontend<0-3> folders, so I moved them into /dev and rebooted.

They are now just plain gone.

Anybody know what's goind on/wrong? What have I broken? ><;;

Ta,

J1M.

EDIT:

Found these?
```

/sys/bus/bttv-sub/devices/dvb0
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/dvb0

```

---

### Post by RoboJ1M on 2006-04-02
I read about MAKEDEV and tried to use it to setup the /dev folder.

I got some errors:
```

/sbin/MAKEDEV: line 2090: major_device-mapper=253: command not found
/sbin/MAKEDEV: don't know what "video4linux" is
/sbin/MAKEDEV: don't know what "alsa" is
/sbin/MAKEDEV: don't know what "rfcomm" is
/sbin/MAKEDEV: don't know what "drm" is
/sbin/MAKEDEV: don't know what "devfs" is
/sbin/MAKEDEV: don't know what "device-mapper" is
/sbin/MAKEDEV: don't know what "mdp" is
/sbin/MAKEDEV: don't know what "video4linux" is
/sbin/MAKEDEV: don't know what "alsa" is
/sbin/MAKEDEV: don't know what "rfcomm" is
/sbin/MAKEDEV: don't know what "drm" is
/sbin/MAKEDEV: don't know what "devfs" is
/sbin/MAKEDEV: don't know what "device-mapper" is
/sbin/MAKEDEV: don't know what "mdp" i

```
Not sure if it's relavent, but it does talk about video4linux

J1M.

---

### Post by RoboJ1M on 2006-04-02
Well, I just reinstalled ubuntu as that module problem was something I did after I first installed, playing with ivtv.

So I re-installed to get rid of any other hidden mistakes.

But I have exactly the same problem, there is no /dev/dvb folder and I get errors about 'don't know what "X" is' when running MAKEDEV.

J1M.

---

### Post by RoboJ1M on 2006-04-02
Fixed it.

For some reason it needs the module dvb_bt8xx loaded but it didn't automatically load it.

I added dst (not sure if it's needed) and dvb_bt8xx to /etc/modules and it seems to work, although I won't be near an aerial until tomorrow.

Anybody know why I had to add it manually?

J1M.

---

### Post by TmP on 2006-04-04
What exactly did you add into modules?
Were can I get some info to understand what stuff like "modules" is responsible for under linux?

I'm having problems installing a leadtek tv2000xp rm card.
I hear it runs on bt878 chipset. I tried to follow this guide:
[http://www.prettymad.net/index.php/How_to_Build_a_MythTV_Box_-_Revised/New/20050918](http://www.prettymad.net/index.php/How_to_Build_a_MythTV_Box_-_Revised/New/20050918)

but i can't get a frequency listing for my network anywhere..
Do you think i could get it from windows? My card works there. Actually it's the only thing holding me back from switching over to Ubuntu..

Damn it's annoying

And about video4llinux - there seems to be a project aiming to write drivers for video cards under linux:
[http://linux.bytesex.org/v4l2/drivers.html](http://linux.bytesex.org/v4l2/drivers.html)
but im too newb to install drivers on my own into Ubuntu. Damn!!

---

### Post by RoboJ1M on 2006-04-04
Hi,

To /etc/modules I added

dst
dvb_bt8xx

And that loads them at boot time.

But before you do that, test that the modules load and are needed by using modprobe

modprobe dst
modprobe dvb_bt8xx

If you post the output of the dmesg command
```

dmesg > ~/dmesg.out 

```
You can compare it to mine and see if there are any errors.
But it kinda sounds like you got your card working.
Post dmesg and we can check.

**Frequency stuff: DVB-T(errestrial)**

Are you in the UK?

Make sure you have installed dvb-utils, this gives you scan and tzap, szap and czap (terrestrial, sattelite and cable)

use this command:
```

sudo find /usr/share -name "uk-*"

```
To locate the files for scan.
Next, change to that folder and have a look. Each file is for one transmitter, prefixed with a country code.

I found out mine by googling for "uk transmitter map" and I found a site where I can enter my post code, it told me I was in the reception area for uk-Rowridge.

so:
```

scan uk-Rowridge > ~/channels.conf

```
Now, in your /home is the channels.conf file.
Load this in a text editor.
My first line reads "BBC ONE"blahblahnumbers

I think it's then tzap "BBC ONE" and lines scroll up the screen, the words FR_HAS_LOCK it the words you are looking for.

Your DVB card is now working.

Use Add Application in the Applications Menu to add Kaffeine (under more... under Sound and Video) and that (might) let you watch DVB. I couldn't watch through it, but it did scan and find all of channels.

It also needs to know your transmitter name.

Or start learning MythTV.
[www.abarbaccia.com](www.abarbaccia.com) is a good guide, but only use from it which packages to load with apt-get.
[This is another good guide]("http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html")
[The real mythtv docs (good)]("http://www.mythtv.org/modules.php?name=MythInstall")
[This is where I learnt the DVB stuff tuning from]("http://www.ethics-gradient.net/myth/mythdvb.html")

What I'm getting from mythtv and dvb on linux so far is Nice Support, Shame About the Documentation.

If I ever contribute anything to planet tux, it won't be code, it will be docs. :)

Regards,

J1M.

---

### Post by TmP on 2006-04-04
Thanx for Your reply!

My dmesg doesn't work for some reason. Here's what i get:
> [4303626.816000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303626.816000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303627.013000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303627.013000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
and it goes on for a few screens. I dont really get it.
I may have my mythbackend running somwhere on the system, unconfigured.

Sadly, I don't live in the UK. But ill look for the frequency anyway. What should it look like? Just one number?

Thanx!

I changed the modules. 
modprobe dvb-bt8xx didn't return anything...
The funny thing is that I get some signal from the composite port - where i connected my laptop tv out. Does this mean anything? Alco the card works under windows, which I'm trying to shake off by installing mythtv.

---

### Post by TmP on 2006-04-04
And about the frequency...

I'm trying to connect to normal analog cable tv. Should I look for the frequency of my cable provider? 

Thanx

---

### Post by RoboJ1M on 2006-04-04
Nope, that's not it, that's something to do with an input device.

I also get those messages, but I get them from my remote control.

Look at my section:
```

[4294695.732000] Linux video capture interface: v1.00
[4294695.820000] bttv: driver version 0.9.15 loaded
[4294695.820000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294695.824000] bttv: Bt8xx card found (0).
[4294695.824000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294695.824000] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 20, latency: 32, mmio: 0xd8001000
[4294695.824000] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[4294695.824000] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[4294695.824000] bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
[4294695.838000] bttv0: using tuner=4
[4294695.863000] bttv0: add subdevice "dvb0"
[4294695.972000] bt878: AUDIO driver version 0.0.0 loaded
[4294695.976000] bt878: Bt878 AUDIO function found (0).
[4294695.976000] ACPI: PCI Interrupt 0000:02:02.1[A] -> GSI 20 (level, low) -> IRQ 20
[4294695.976000] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 20, latency: 32, memory: 0xd8002000
[4294696.088000] ACPI: PCI Interrupt 0000:02:05.0[A] 

```
The v4l (Video For Linux, everything to do with capture) section starts with
**"Linux video capture interface: v1.00"**

First it loads **"bttv: driver version 0.9.15 loaded"** for all BT8x8 based cards.

This is an importane line [B]"bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
"[/B]

After that, it loads dst and dvb_bt8xx and says that it's registering adapter0, but it's not in that cutting.

But find the v4l section.

J1M.

---

### Post by TmP on 2006-04-04
Ok, found it:

> [4294711.920000] Linux video capture interface: v1.00
[4294712.054000] bttv: driver version 0.9.15 loaded
[4294712.054000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294712.058000] bttv: Bt8xx card found (0).
[4294712.059000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294712.059000] PCI: setting IRQ 5 as level-triggered
[4294712.059000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (le vel, low) -> IRQ 5
[4294712.059000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 5, latency: 32, mmi o: 0xde000000
[4294712.059000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID  is 107d:6609
[4294712.059000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,au todetected]
[4294712.059000] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[4294712.106000] bttv0: using tuner=5
[4294712.106000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294712.108000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294712.110000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294712.112000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294712.162000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294712.162000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compati bles))
[4294712.270000] bttv0: registered device video0
[4294712.275000] bttv0: registered device vbi0
[4294712.281000] bttv0: registered device radio0
[4294712.281000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294712.318000] bttv0: add subdevice "remote0"
[4294712.335000] bt878: AUDIO driver version 0.0.0 loaded
[4294712.338000] bt878: Bt878 AUDIO function found (0).
[4294712.338000] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [LNKB] -> GSI 5 (le vel, low) -> IRQ 5
[4294712.338000] bt878(0): Bt878 (rev 17) at 00:09.1, irq: 5, latency: 32, memor y: 0xde001000
[4294716.608000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294718.410000] cdrom: hdc: mrw address space DMA selected
[4294718.412000] cdrom open: mrw_status 'not mrw'
]


I hope that's it. 
I found this guide, I'm trying to follow it:
[http://tvtime.sourceforge.net/problems.html#undetecte](http://tvtime.sourceforge.net/problems.html#undetecte)

Thanx for Your help,
I really appreciate it

---

### Post by RoboJ1M on 2006-04-04
Ah, I've just read your post about this being analogue cable. (missed it earlier)

I don't know anything about analogue tuners.
As far as I know, they are far better supported both by driver and application.

But I couldn't tell you which application (apart from MythTV)

As far as I know, all that stuff I posted about DVB-T tuning is *just* for DVB-T.

I believe these are the important "it works now" lines:
```

[4294712.270000] bttv0: registered device video0
[4294712.275000] bttv0: registered device vbi0
[4294712.281000] bttv0: registered device radio0

```
Those are the lines (but for dvb) that magically appeared when I loaded dvb_bt8xx and it all worked after that.

As far as I can tell, you're all set to start watching tv.

Regards,

J1M.

---

### Post by TmP on 2006-04-04
Thanx a bunch!


I just found a myth tv community in my country of origin. They keep a xmltv channal guide.

---

### Post by RoboJ1M on 2006-04-04
Your secret country of origin? :D

*What are you hiding from us!* :@

J1M.

---

