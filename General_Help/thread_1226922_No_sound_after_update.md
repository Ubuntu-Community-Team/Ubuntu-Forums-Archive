---
title: "No sound after update"
date: 2009-07-30
forum: General Help
---

### Post by Cthulhu_Dreams on 2009-07-30
After this latest update (I think it was headers) my sound simply stopped working.  I have no clue what the issue is, and no its not muted. Last time I had a similar issue, and if I recall something during the updated turned off my audio settings...but I can't remember how to fix it. I tried reinstalling ALSA, no luck.  I'm not too familiar with Ubuntu, so try not to make any response TOO complicated. ;)

Any hoo:

aplay -l

```
adrian@Alpha-60:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
adrian@Alpha-60:~$ 

```

lspci -v

```
adrian@Alpha-60:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, fast devsel, latency 0, IRQ 2296
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 7110 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, fast devsel, latency 0
    Memory at d5400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 70e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 70c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at da505c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at da500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d9500000-da4fffff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d8500000-d94fffff
    Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d7500000-d84fffff
    Prefetchable memory behind bridge: 00000000d2400000-00000000d33fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d6500000-d74fffff
    Prefetchable memory behind bridge: 00000000d3400000-00000000d43fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d5500000-d64fffff
    Prefetchable memory behind bridge: 00000000d4400000-00000000d53fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 70a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 7080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 7060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 7040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at da505800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2298
    I/O ports at 7108 [size=8]
    I/O ports at 711c [size=4]
    I/O ports at 7100 [size=8]
    I/O ports at 7118 [size=4]
    I/O ports at 7020 [size=32]
    Memory at da505000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: medium devsel, IRQ 11
    Memory at da506000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 7000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: fast devsel, IRQ 11
    Memory at da504000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d9500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3627
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    I/O ports at 5000 [size=256]
    Memory at d1410000 (64-bit, prefetchable) [size=4K]
    Memory at d1400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1420000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

lsmod:

```
adrian@Alpha-60:~$ lsmod
Module                  Size  Used by
cbc                    12288  407 
aes_x86_64             16384  408 
aes_generic            36264  1 aes_x86_64
ecb                    11392  1 
i915                   75528  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
ipt_REJECT             11776  1 
ipt_LOG                14468  1 
xt_limit               11140  2 
xt_tcpudp              11776  7 
xt_state               10624  5 
ipt_addrtype           11136  4 
ip6table_filter        11264  1 
ip6_tables             29712  1 ip6table_filter
nf_nat_irc             10752  0 
nf_conntrack_irc       14648  1 nf_nat_irc
nf_nat_ftp             11520  0 
nf_nat                 30100  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      24216  7 nf_nat
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
nf_conntrack_ftp       17592  1 nf_nat_ftp
nf_conntrack           84752  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         11392  1 
ip_tables              28304  1 iptable_filter
x_tables               31624  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  4 
leds_hp_disk           11400  0 
uvcvideo               69640  0 
led_class              13064  1 leds_hp_disk
psmouse                64028  0 
snd_pcm                99464  2 snd_hda_intel
snd_timer              34064  1 snd_pcm
snd                    78920  10 snd_hda_intel,snd_pcm,snd_timer
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
joydev                 20864  0 
ieee80211_crypt_tkip    17920  0 
pcspkr                 11136  0 
soundcore              16800  1 snd
iTCO_wdt               21712  0 
v4l1_compat            23940  2 uvcvideo,videodev
serio_raw              14468  0 
wl                   1286352  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
iTCO_vendor_support    12420  1 iTCO_wdt
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
video                  29204  0 
intel_agp              39408  1 
output                 11648  1 video
lis3lv02d              19408  0 
usb_storage           115392  0 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

---

### Post by Soul-Sing on 2009-07-30
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

---

### Post by Cthulhu_Dreams on 2009-07-30
E: Couldn't find package linux-ubuntu-modules-2.6.28-14-generic

---

### Post by Soul-Sing on 2009-07-30
would you please run a ```
sudo apt-get update
```

---

### Post by arikg on 2009-07-30
same problem here. lost sound after the last update

---

### Post by arikg on 2009-07-30
modifying /boot/grub/menu.lst to boot with 2.6.28-13 does not solve the problem ...

the last update completely broke my X200s laptop - no sound, and the laptop hangs on restart or shut down.

anyone has a clue?

---

### Post by Cthulhu_Dreams on 2009-07-30
> would you please run a

Done, and I re ran that original command; no effect, same output.

---

### Post by arikg on 2009-07-30
Switching from ALSA to OSS in System->Preferences->Sound gives me back my sound in music/movie players, but I am not happy with this solution.

Many applications need ALSA. Skype still not working ...

---

### Post by mathd on 2009-07-30
I have the exact same problem.

sudo apt-get install linux-ubuntu-modules-`uname -r`

give me the could not found package.

E: Impossible de trouver le paquet linux-ubuntu-modules-2.6.28-14-server

---

### Post by Cthulhu_Dreams on 2009-07-30
I tried asking on IRC but everyone is unhelpful on there.  Anyone got a solution here?

---

### Post by stovicek on 2009-07-30
That's because linux-ubuntu-modules-* packages only apply to Hardy. Since then, the modules are split between restricted and backports packages. 

However, I had an issue similar to this not too long ago after an update. I had read the same suggestions and tried to no avail. As it turns out, my audio chipset also allows for Switches to turn the speakers and headphones on and off. Even though I made sure nothing was muted, sound was still not working. 

My audio device:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My solution:
Opened the Volume Control, set the Device for HDA Intel (Alsa mixer), clicked on Preferences button. From a rather long list of tracks with their corresponding area, scrolled down to Headphone and Speaker for Switches. Enabled both of those and a new tab appeared on the Volume Control mixer called Switches. Enabled Headphone and Speaker. Sound commenced.

---

### Post by Cthulhu_Dreams on 2009-07-30
Scratch that, I found volume control, although the options you suggested weren't there, and the ones that were didn't enable the sound. DAMN.

---

### Post by Cthulhu_Dreams on 2009-07-30
I think it has something to do with ACPI.  Apparently other people were having similar problems, and they found out that ACPI managerment had disabled the hardware.  They put acpi=force pci=noacpi into their boot options in grub and it worked...

---

### Post by hermanus on 2009-07-31
Solved. Lost sound after upgrade yesterday. Fixed after uninstall - install Pulse Audio on Dv6 HP laptop. (Alsa updated to latest alsa snapshot, but don't think that was the fix.)

---

### Post by Cthulhu_Dreams on 2009-07-31
I'm ridiculously frustrated with this problem, so I think I better take a break before I throw my f*cking laptop out the window.

I tried removing pulseaudio and reinstalling it, that didn't fix anything for me.  I too am using a dv6, so I think its just an issue with the model (as the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") guide said)  I copied and pasted those commands into the terminal and I don't think it worked.

I got to "./configure"

When I got this message:

checking for current directory... /home/adrian/src/alsa/alsa-driver
checking cross compile... 
checking for directory with kernel source... ./configure: line 4948: cd: /usr/src/linux: No such file or directory
/usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

After which I let out a string of obscenties and did a few rounds with my punching bag.

Could you post some outputs hermanus?  I'd like to see what your alsa-base.conf has in it, as well as the usual "aplay -l" and "lspci -v" stuff.  Also, what are you using under Sound Preferences?

---

### Post by hermanus on 2009-07-31
I understand the frustration. Here are some outputs and I'll explain what I do below:

alsa-base-conf
=================
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
=====================

I added the last 4 lines to the above

aplay -l
======================
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
===========================

lspci -v     relevant parts I think??
============
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3628                                   
        Flags: bus master, fast devsel, latency 0, IRQ 2295                              
        Memory at da100000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel  


----
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
        Subsystem: Hewlett-Packard Company Device 3628                              
        Flags: bus master, fast devsel, latency 0, IRQ 2293                         
        Memory at da010000 (32-bit, non-prefetchable) [size=16K]                    
        Capabilities: <access denied>                                               
        Kernel driver in use: HDA Intel                                             
        Kernel modules: snd-hda-intel  

================================================
 

What I do.

I regularly update alsa getting it from:
[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

Then extract, go to folder, install by:

./configure --enable-dynamic-minors
make
make install
-------------------
and add this to end of /etc/modprobe.d/alsa-base.conf 

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1


Under Sound Preferences (in Kubuntu) I'm using PulseAudio

This gets sound working out of speakers only, not headphone jack. To get it working out of jack or other options I use this workaround from from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870).

You need to get hda-verb (google it) and just run the appropriate commands in terminal. Clumsy, but works.

#activate the sound on the speaker
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_data 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_dir 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_mask 1

#activate the sound on the headset
sudo ./hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1

#mute the speaker
sudo ./hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0
#unmute the speaker
sudo ./hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0x40

#mute the headphones
sudo ./hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0
#unmute the headphones
sudo ./hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0x40

I hope this helps.

---

### Post by hermanus on 2009-07-31
Oooops...did reboot,no sound...the above worked predictably before yesterday's upgrade.

---

### Post by mister_p_1998 on 2009-07-31
I updated Intrepid to Koala, killed the sound, Koalas crap in this respect, dont rate Intrepid high either, I use LTS Hardy on my working machine, Intrepid & Koala are on the test box.
Steve

---

### Post by arikg on 2009-07-31
Cthulhu_Dreams,

The only solution I have found is to switch to OSS. It is not ideal, but it works. Go to system>>preferences>>sound, choose OSS and hit a test sound. 

does it work for you?

---

### Post by Ericj1186 on 2009-08-01
My issue is similar to the ones listed, but so much worse.

I loaded Youtube today, and there was no sound. I check the corner box, and the sound is Xed out.  So, I unmute it and get this:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Ok... 

So, I head to Sound Preferences.  There are no default devices there.  I run this lshw -C sound:

```
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=5 mingnt=4

```My computer was running flawlessly with ALSA sound a few days ago, and now, I can't get any sound at all.

I tried to revert to 2.6.28-13, but when I do, I am stuck in the terminal like with this topic [http://ohioloco.ubuntuforums.org/showthread.php?t=1159188](http://ohioloco.ubuntuforums.org/showthread.php?t=1159188).  I tried my fix that got me out of it, and it still didn't work.

Does anyone have any suggestions to fix this?

To add: I have no issues in Windows with sound.  Full surround sound.  Sigh...

---

### Post by Ericj1186 on 2009-08-01
> **Ericj1186 said:**
> My issue is similar to the ones listed, but so much worse.

I loaded Youtube today, and there was no sound. I check the corner box, and the sound is Xed out.  So, I unmute it and get this:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Ok... 

So, I head to Sound Preferences.  There are no default devices there.  I run this lshw -C sound:

```
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=5 mingnt=4

```My computer was running flawlessly with ALSA sound a few days ago, and now, I can't get any sound at all.

I tried to revert to 2.6.28-13, but when I do, I am stuck in the terminal like with this topic [http://ohioloco.ubuntuforums.org/showthread.php?t=1159188](http://ohioloco.ubuntuforums.org/showthread.php?t=1159188).  I tried my fix that got me out of it, and it still didn't work.

Does anyone have any suggestions to fix this?

To add: I have no issues in Windows with sound.  Full surround sound.  Sigh...

Problem solved... I restarted this morning to 2.6.28-13, and it worked fine.  I didn't do anything different.  Linux is just screwing with me.

---

### Post by wulfman on 2009-08-01
a lenovo t400 here suffers a similar problem since the last reboot. it had pulseaudio-problems before, but mostly worked. now sound is completely broken (just a buzzing sound, like something is electrocuted), unless everything is set to OSS. 

pretty annoying - any ideas?

mfg
wulfman

---

### Post by Ed187 on 2009-08-01
I too am having a sound problem.  Headphones work, but speakers don't.:(

---

### Post by Ericj1186 on 2009-08-02
Two guys above me:  Did you try kernel 2.6.28-13?  If that one still works, I'd suggest using it until your cards become supported or a fix is found.

What brand cards are you two using?

---

### Post by Cthulhu_Dreams on 2009-08-03
I tried going back to .13 and it didn't help, although I've tried so many things I may have screwed it up somewhere.

---

### Post by Ericj1186 on 2009-08-03
On .13, does it show any devices at all under Sound Preferences? (System>Preferences>Sound)  Are you still getting the GStreamer error?

What card are you using?

---

### Post by wulfman on 2009-08-03
thanks for listening in.

booting into  .13 or .11 did not help. the card is identified as an Intel High Definition Audio (lenovo T400 notebook), and yes, it still shows up as an audio device.

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0mfg
w

---

### Post by Cthulhu_Dreams on 2009-08-03
Interestingly, I'm getting sound again in .13.  Didn't do anything, not sure why.  Still I'd like to get 14 (or was it 15?) working.

---

### Post by Quarkrad on 2009-08-04
I too had no sound after an upgrade; this worked for me.  Open terminal and type:

alsamixer

use keyboard arrows (left/right) to move across and (up/down arrows) to adjust volumes.

---

### Post by wulfman on 2009-08-04
well, it is possible to get sound (mostly) back by switching to oss, but pulseaudio remains dead. which it shouldn´t do, nowadays...

mfg
w

---

