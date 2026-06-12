---
title: "Audio not working for speakers, but works for heaphones"
date: 2012-09-15
forum: General Help
---

### Post by bobdotexe on 2012-09-15
hey guys I have Ubuntu 12.04 64bit, and I've been having speaker issues for a while, some times my speakers would make all my sounds sound high pitch and ringy. hard to explain, like the sound you hear when a gba game gets removed when a game is playing...

any way, later on I started getting a constant clicking sound that would repad about every 9 seconds coming from the speakers and from headphones inf plugged in.

but then recently in the middle of a youtube video my speakers just stopped. SO I restarted my pc, and they would still not work, I plugged in some headphones, and they worked fine (clicking gone)
but the speakers no longer will work.

I booted back to windows, and they seemed to be ok (never had a clicking issue in win7)

So I checked out some post and most said to use Alsamixer to check vol levels, I did that, they were all at max, some others suggested re-installing(uninstall+purge, then reinstall) Alsa (all packages) and pulse audio too,
I tried that followed by a reboot and still no luck,
I later found this:
[COLOR="Blue"][https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)[/COLOR]
and followed all it's steps and all sub catagores (except the nvida and midi) and no luck.

any ideas?
any help would be appreciated.

```

PC: HP dv6t
processor:core i5-64bit
OS: Ubuntu 12.04
Desktop:Gnome 3

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```
[this issue has been resolved]
Solution:
[http://ubuntuforums.org/showpost.php?p=12246625&postcount=5](http://ubuntuforums.org/showpost.php?p=12246625&postcount=5)

---

### Post by carranty on 2012-09-17
It seems very strange to me that your headphones would work perfectly while your speakers don't, are you plugging the headphones into the same output (3.5mm jack) as the speakers?  Or are you using both at the same time?  If the former I would say its a fault with the speakers, though if they work in windows I guess it can't be. If its the latter, have you opened up 'sound preferences' and made sure your sound card is configured correctly?

---

### Post by bobdotexe on 2012-09-17
> **carranty said:**
> It seems very strange to me that your headphones would work perfectly while your speakers don't, are you plugging the headphones into the same output (3.5mm jack) as the speakers?  Or are you using both at the same time?  If the former I would say its a fault with the speakers, though if they work in windows I guess it can't be. If its the latter, have you opened up 'sound preferences' and made sure your sound card is configured correctly?

yeah in Ubuntu 11.04 I would sometimes have to manually switch between headphones and speakers, the option was removed in 11.10 I think and it would have one option that would switch automatically.

maybe whatever switches between headphones/speakers is not working.
it would auto switch till about 2 weeks ago, I plugged in a usb headphone adapter that came with my new headphones:
[http://www.amazon.com/gp/product/B0041OQKIC/ref=oh_details_o03_s00_i00](http://www.amazon.com/gp/product/B0041OQKIC/ref=oh_details_o03_s00_i00)
after that I unplugged it, and my built-in sound card got stuck on speakers.


also here is a copy of my '/etc/modprobe.d/alsa-base.conf':
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
#fix hopefully
options snd_hda_intel model=mobile
```

even though the speakers don't work they still make a clicking sound when no headphones are plugged in

and the headphones make a similar sound until I play some audio.

speaker sound:
[https://docs.google.com/open?id=0B0ZioqQbPi-MX3FxUkFXWU0xTDg](https://docs.google.com/open?id=0B0ZioqQbPi-MX3FxUkFXWU0xTDg)

---

### Post by bobdotexe on 2012-09-18
I changed the last line to: 'options snd_hda_intel model=generic'
that makes the speakers work, but the headphones will not output any sound. sound still comes out of the speakers .

---

### Post by bobdotexe on 2012-09-18
I finally found the fix!
[https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/24639](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/24639)
post number 11.
turn off RTC in /etc/modules  !!!
so All I had to do was comment out one line!

---

