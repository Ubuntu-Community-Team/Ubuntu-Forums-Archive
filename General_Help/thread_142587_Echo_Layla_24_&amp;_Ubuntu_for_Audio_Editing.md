---
title: "Echo Layla 24 &amp; Ubuntu for Audio Editing?"
date: 2006-03-10
forum: General Help
---

### Post by scottevan on 2006-03-10
Hi, I am considering swapping from Windows XP to Ubuntu, but I need to be able to use an **Echo Layla 24** for audio editing. Will I be able to find drivers for this hardware? Please help me out with some suggestions! Thanks, Scott

---

### Post by ThrashJazzAssassin on 2006-06-24
This is a page from the wiki [https://wiki.ubuntu.com/EchoMia]("https://wiki.ubuntu.com/EchoMia")
Which shows steps how to install an Echoaudio mia card. 

I couldn't get it to work with my echoaudio Darla20 card though:(

---

### Post by ronoc on 2006-07-09
I am just about to attempt to install Echo layla 24 drivers on a Toshiba Sat pro A100 with Dapper 6.06. The Layla should interface with the PCMCIA card.  Does anyone have suggestions?
I was going to follow the info given here
[http://www.ubuntuforums.org/showthread.php?t=142587&highlight=layla](http://www.ubuntuforums.org/showthread.php?t=142587&highlight=layla)
and
[http://www.webalice.it/g_pochini/ead/](http://www.webalice.it/g_pochini/ead/)

---

### Post by scottevan on 2006-07-09
Yeah. That is what I was using too. It hasn't worked for me yet, but i am new to linux and don't have a strong grasp on all the basics of troubleshooting.

So far, I have just managed to mess up the existing configuration so that I now have no working sound :(

Let us know if it works for you!

---

### Post by rakeen on 2006-07-10
> **scottevan said:**
> Yeah. That is what I was using too. It hasn't worked for me yet, but i am new to linux and don't have a strong grasp on all the basics of troubleshooting.

So far, I have just managed to mess up the existing configuration so that I now have no working sound :(

Let us know if it works for you!

Hello,

Have you see that thread ?

[http://www.ubuntuforums.org/showthread.php?t=199599](http://www.ubuntuforums.org/showthread.php?t=199599)

It's for echo mia under ubuntu dapper, but I think what mia and Layla 24 have the same chip (motorola).

Bye

---

### Post by ronoc on 2006-07-10
I have and I have followed it. 
just so there is no confusion this is what I have been looking at.

[http://www.ubuntuforums.org/showthread.php?t=199599](http://www.ubuntuforums.org/showthread.php?t=199599)

I have now downloaded the kernel headers. These did not have the version.h therefore with the --with-kernel= option I could set the path to the headers which are already on /usr/include/linux which version.h resides. 
When i attempt to configure the soundcard is unrecognized -Layla24, Layla, Layla.
Two questions - what is Oss emulation?
Secondly how can i query to find out what soundcards are supported.

---

### Post by ronoc on 2006-07-11
Does anyone have intention of answering this please ... please

---

### Post by ronoc on 2006-07-16
I got it working sweet!

Scott, give me a full explanation of where you got to and I will point you from there.

can you load the module without raising any errors>
> sudo modprobe snd-layla24

Are you on a desktop or a laptop?
i.e hotplug support for the PCMCIA adapter or straight PCI?

Get hwinfo from synaptic
after it is installed run it

>hwinfo

This should give you list of stuff.
up towards the top of the list you will find the echo details

can you see something like

[4294690.863000] Echoaudio Layla24: probe of 0000:08:00.0 failed with error -2
[4294691.751000] NET: Registered protocol family 17
[4294695.228000] lp: driver loaded but no devices found
[4294695.264000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294695.264000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294695.264000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294695.295000] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k

---

### Post by scottevan on 2006-07-17
hi ronoc,

thanks sooooo much for offering to help. i have been on the verge of giving up on ubuntu (which i really like overall).

i am able to load the module without error (do i have to do this everytime i restart?).

im using a laptop & pcmcia card. here is the hwinfo:

> 30: PCI 400.0: 0480 Multimedia controller
  [Created at pci.277]
  UDI: /org/freedesktop/Hal/devices/pci_1057_3410
  Unique ID: YmUS.WgIgdYU+GZ6
  Parent ID: x0Ln.1uqn+uuLox6
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: unknown
  Model: "Echo Digital Audio Layla24"
  Hotplug: CardBus
  Socket: 0
  Vendor: pci 0x1057 "Motorola"
  Device: pci 0x3410 "DSP56361 Digital Signal Processor"
  SubVendor: pci 0xecc0 "Echo Digital Audio Corporation"
  SubDevice: pci 0x0060 "Layla24"
  Revision: 0x01
  Memory Range: 0x32000000-0x320fffff (rw,non-prefetchable)
  IRQ: 177 (7 events)
  Module Alias: "pci:v00001057d00003410sv0000ECC0sd00000060bc04sc80i00"
  Driver Info #0:
    Driver Status: snd_layla24 is active
    Driver Activation Cmd: "modprobe snd_layla24"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (CardBus bridge)


using the revised [EchoMia community documentation]("https://help.ubuntu.com/community/EchoMia") i have been able to get everything installed without error and i can now access the alsa mixer. at this point things seem to be configured, i just cant figure out why sound isnt going through the layla. (i think that nothing is muted... i should be able to unmute simply by pressing 'm' in the alsa mixer, right?)

any suggestions would be greatly appreciated!

thanks again for your help!
scott

---

### Post by ronoc on 2006-07-17
Hi Scott,
I know, I was on the verge of tears with this.

Have you installed the echomixer through synaptic?
What do you get when you 
>> aplay -l

Is the echo card loaded.

---

### Post by ronoc on 2006-07-17
everything looks good on the alsamixer, after installing echomixer, try to launch

> echomixer

if it returns witha no echo cards detected error

try

>dmesg

scott, and see if the firmware is loaded properly.

---

### Post by scottevan on 2006-07-17
ronoc,

echomixer seems to be installed. i can now launch it with "echomixer" at the terminal.

aplay -l outputs this:
> **** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Layla24 [Layla24], device 0: Analog PCM [Layla24]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Layla24 [Layla24], device 1: Digital PCM [Layla24]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7


and dmesg outputs a very long list of stuff like this:
> [17202352.628000] printk: 23 messages suppressed.
[17202352.628000] sg_write: data in/out 30576/30576 bytes for SCSI command 0xbe--guessing data in;
[17202352.628000]    program rhythmbox not setting count and/or reply_len properly
[17202358.644000] printk: 35 messages suppressed.
[17202358.644000] sg_write: data in/out 30576/30576 bytes for SCSI command 0xbe--guessing data in;
[17202358.644000]    program rhythmbox not setting count and/or reply_len properly


Thanks,
Scott

---

### Post by ronoc on 2006-07-17
do you see any sign of any information on the layla from the dmesg output

---

### Post by scottevan on 2006-07-17
Ok, after a great deal of searching i did find a reference to the layla24, but it isn't clear to me that it is an error. actually, im not sure where the layla related content starts and stops... so here is the reference in context:
> [17179587.840000] pccard: CardBus card inserted into slot 0
[17179587.904000] cs: IO port probe 0x100-0x4ff: excluding 0x370-0x377 0x3f0-0x3f7
[17179587.904000] cs: IO port probe 0xc00-0xcf7: clean.
[17179587.908000] cs: IO port probe 0xa00-0xaff: clean.
[17179587.936000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[17179587.936000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[B][17179588.188000] ALSA /home/kila/Desktop/alsa-driver-1.0.12rc1/pci/echoaudio/echoaudio.c:2010: Card registered: Layla24 rev.0 (DSP56361) at 0x32000000 irq 177
[/B][17179588.784000] lp: driver loaded but no devices found
[17179588.832000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179588.832000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179588.832000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179588.860000] Adding 867468k swap on /dev/sda6.  Priority:-1 extents:1 across:867468k

im guessing that the surrounding lines relate to other devices? also, attached is a screenshot of the echomixer, in case i am just doing something stupid :)

thanks again for your generous assistance!

---

### Post by ronoc on 2006-07-18
It looks from the screenshot that your channels one and two might be muted (off).
The inputs and outputs panel with the grey buttons. Both 1 and 2 should be pushed in.

What are you using to test your card. Are you sure the app is not still trying to use the build in card on board. I know i have one of those Intel realtek soundcards and I can't get it to work. Although I have not tried properly the focus  has been onthe layla. I use PD and with this I could for definite select the layla and test the input and output.

---

### Post by adds2one on 2006-08-05
Hello,

Could anyone who has successfully installed an Echo Audio sound card please check out my post for help with an Indigo IO [http://www.ubuntuforums.org/showthread.php?t=229778](http://www.ubuntuforums.org/showthread.php?t=229778)

Much appreciated, - J

---

