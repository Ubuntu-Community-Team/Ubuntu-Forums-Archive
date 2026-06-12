---
title: "Skype &amp; VirtualBox - cant start &amp; forcing logout, ubuntu 10.10"
date: 2010-11-01
forum: General Help
---

### Post by examon on 2010-11-01
Hello guys... ive got kinda big problem...
At the first i want to say that im really noob about ubuntu, installed this linux distrubution some days ago and I really like it but ive got two really big problems.

So... after I installed 10.10 I installed skype 2.1, and VirutalBox and everything seems ok... they worked really good, no problems but yesterday I wanted to start skype and it just failed.. no error messages nothing... it just forced system to logout... when I logged in and started skype again... same problem... then I reinstalled skype... same problem... I installed older version... same problem...
Today I wanted to run my VirtualBox with winXP cos I need it for some applications and it just forced unbuntu logout but b4 some days ago it worked really good... again same no error messages... same like with skype...

This is really big problem for me cos I need both, skype and virtualbox, working... I really like this new ubuntu but I just need this two apps and they just cant run...

Really thanks for help guys... I know mb this problem will be easy fixable for you but as I sad... im ubuntu noob :)

---

### Post by sd3250 on 2010-11-04
i have the same problem, don't know how to fix this :(

---

### Post by sd3250 on 2010-11-04
i think that xorg crashes, i see a seg fault in the log file:
[  4046.178] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
[  4046.178] 1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
[  4046.178] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x15940c]
[  4046.178] 3: /usr/bin/X (0x8048000+0x26087) [0x806e087]
[  4046.178] 4: /usr/bin/X (0x8048000+0x1a5ba) [0x80625ba]
[  4046.178] 5: /lib/libc.so.6 (__libc_start_main+0xe7) [0x274ce7]
[  4046.178] 6: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
[  4046.178] Segmentation fault at address 0x4
[  4046.187] 
Caught signal 11 (Segmentation fault). Server aborting
[  4046.187] 
Please consult the The X.Org Foundation support


lspci: 
root@zero:/var/log# lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
root@zero:/var/log# 

lsmod:
root@zero:/var/log# lsmod
Module                  Size  Used by
ip6table_filter         1275  0 
ip6_tables             11764  1 ip6table_filter
ipt_MASQUERADE          1419  3 
iptable_nat             3752  1 
nf_nat                 16289  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10783  4 iptable_nat,nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
xt_state                1014  1 
nf_conntrack           63258  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2004  2 
xt_tcpudp               1927  4 
iptable_filter          1302  1 
ip_tables              10460  2 iptable_nat,iptable_filter
x_tables               15921  9 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,ip_tables
bridge                 68008  0 
stp                     1667  1 bridge
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
binfmt_misc             6599  1 
nvidia               9329739  35 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
hid_a4tech              2018  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
parport_pc             26058  1 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
video                  18712  0 
output                  1883  1 video
led_class               2633  0 
serio_raw               4022  0 
intel_agp              26360  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  2 hid_a4tech,usbhid
floppy                 54311  0 
r8169                  36489  0 
mii                     4425  1 r8169
root@zero:/var/log#

---

### Post by sd3250 on 2010-11-05
from what i found out it is a bug in the nvidia driver and it appears if you use two monitors and/or xinerama

---

### Post by j33pn on 2010-11-05
I'm having the same problem, and I'm using nvidea drivers, and I'm using two monitors, and xinerama.

When I move the the cursor onto the Skype EULA window the screens go black for a few seconds and then they come back on and I'm at the login screen.

Yesterday, I found I have the same problem with KTurtle, the educational program, which I was looking forward to sharing with my 8 year-old.


Is this something that can't be fixed, b/c it's Nvidea's problem, or is this a bug worth reporting?  Where do we go from here?

---

### Post by j33pn on 2010-11-05
Also, I forgot to add, that On a different physical drive in this same laptop (It's a big HP laptop with two physical drives), I installed and use Skype with no problem on Ubuntu 10.04 just a week or two ago (with two screens and nvidea drivers and xinerama).  I still have that installation available if it could help troubleshoot the difference between 10.10 and 10.04.  I just don't know how to go about it.

---

### Post by alankstewart on 2010-11-07
I also see the bug using the nvidia driver with two monitors AND xinerama on. If xinerama is off, two monitors (with a duplicated desktop) does not cause the log out issue.

---

### Post by asdlkf on 2010-11-13
I can confirm that disabling xineorama fixed this issue.

The symptoms I was experiencing: 

I was running dual-head setup with xineorama enabled on an NVIDIA 8800 GTS 320m.

I installed and launched mumble (with my mouse away from the application). 

The application appeared to open correctly. When I placed my cursor over the application, I would be logged out and GDM would crash. 

Due to the lack of failure output (just logged out), I stopped GDM and manually "startx"ed. I reproduced the issue and when X crashed, the TTY I was logged into spit out a segfault message.

I then found this article, disabled xineorama (I left dual head enabled, but the other monitor is running as a separate x session). 

The issue is no longer occurring.

---

### Post by trickylogician on 2010-11-15
Having the same issue with 10.10/nvidia/xinerama/virtualbox. Should we report a bug with everyone involved in hopes that someone will fix this? 

My second monitor is useless without xinerama, because it is mounted rotated 90 degrees. My backup drive is useless without 10.10 because in 10.4 my transfer rate was less than a megabyte per second. My life would be fairly sad without virtualbox, given that I need to run various terrible windows programs for school that don't work in wine, and I was working on a LFS build in a virtualbox prior to upgrading. It takes webpages approximately 90 seconds to load without the proprietary drivers installed.

If anyone knows how to rotate one monitor and not the other without using xinerama, that would solve the problem as far as I am concerned.

---

### Post by curaloucura on 2010-11-19
I'm having the same problem. Tried using an older version of the NVidia driver but no luck.
Not sure where to look for help.

---

### Post by curaloucura on 2010-11-24
No solution for Skype, but I ended up using VBoxGtk and it's working fine

[http://sourceforge.net/projects/vboxgtk/](http://sourceforge.net/projects/vboxgtk/)

---

