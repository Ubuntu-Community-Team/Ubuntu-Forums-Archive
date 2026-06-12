---
title: "Configuring Soundcard"
date: 2006-04-28
forum: General Help
---

### Post by xMikey on 2006-04-28
I have no sound.  So I'm guessing that my soundcard isn't configured?  Anyone want to help me with this one?  Yes, I've already searched Google and these forums, and either I suck at searching...or I'm just having bad luck at the moment.  I've used Ubuntu in the past, but had to get rid of it for certain reasons, now I'm back on it...and need some help.  ](*,) 

Terminal Commands-

ps -e
```
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
   22 ?        00:00:00 kacpid
   91 ?        00:00:01 kblockd/0
  127 ?        00:00:04 pdflush
  129 ?        00:00:00 aio/0
  128 ?        00:00:05 kswapd0
  716 ?        00:00:00 kseriod
 1090 ?        00:00:11 kjournald
 3240 ?        00:00:00 khubd
 3806 ?        00:00:00 dhclient3
 4245 tty2     00:00:00 getty
 4246 tty3     00:00:00 getty
23891 ?        00:00:00 gdm
23892 ?        00:00:00 gdm
24021 ?        00:20:34 Xorg
24087 tty4     00:00:00 getty
24088 tty5     00:00:00 getty
24089 tty6     00:00:00 getty
24153 tty1     00:00:00 getty
24160 ?        00:00:01 x-session-manag
24205 ?        00:00:00 ssh-agent
24208 ?        00:00:00 dbus-launch
24209 ?        00:00:00 dbus-daemon-1
24211 ?        00:00:06 gconfd-2
24214 ?        00:00:00 gnome-keyring-d
24220 ?        00:00:03 gnome-settings-
24233 ?        00:00:02 xscreensaver
24244 ?        00:00:01 gnome-smproxy
24252 ?        00:00:21 metacity
24269 ?        00:00:18 nautilus
24279 ?        00:00:01 gnome-cups-icon
24292 ?        00:00:00 mapping-daemon
28381 ?        00:00:04 pdflush
30367 ?        00:00:00 gnome-vfs-daemo
30411 ?        00:00:05 hald
  915 ?        00:00:41 gam_server
14230 ?        00:00:00 udevd
21931 ?        00:00:00 atd
21969 ?        00:00:00 cron
24478 ?        00:00:00 hcid
24488 ?        00:00:00 sdpd
24500 ?        00:00:00 krfcommd
27510 ?        00:00:00 inetd
27760 ?        00:00:00 dd
27762 ?        00:00:00 klogd
27830 ?        00:00:00 syslogd
28009 ?        00:00:00 master
28012 ?        00:00:00 pickup
28013 ?        00:00:00 qmgr
28321 ?        00:00:00 dbus-daemon
28334 ?        00:00:00 hald
28339 ?        00:00:00 hald-addon-acpi
28348 ?        00:00:00 hald-addon-stor
28350 ?        00:00:00 hald-addon-stor
28564 ?        00:00:00 acpid
29930 ?        00:00:00 hpiod
29933 ?        00:00:00 python
32580 ?        00:00:00 cupsd
 4487 ?        00:00:10 gnome-panel
 4493 ?        00:00:00 bonobo-activati
 4519 ?        00:00:06 wnck-applet
 4521 ?        00:00:00 trashapplet
 4524 ?        00:00:00 gnome-vfs-daemo
 4536 ?        00:00:00 clock-applet
 4539 ?        00:00:01 mixer_applet2
 4644 ?        00:00:00 notification-ar
 8023 ?        00:00:28 gaim
 8049 ?        00:01:04 opera
 8083 ?        00:00:01 gnome-terminal
 8085 ?        00:00:00 gnome-pty-helpe
 8086 pts/0    00:00:00 bash
 8100 ?        00:00:06 nautilus
 8183 ?        00:00:00 operamotifwrapp
 8184 ?        00:00:00 operapluginclea
 8312 pts/0    00:00:00 ps

```

lspci
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 22)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:04.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
0000:00:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device 4310
0000:00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
0000:00:0b.2 Input device controller: Rockwell International: Unknown device 4312
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

```
That enough information?  Or do I need to do something else?  Oh, also, my computer is really old and a piece of crap...so yeah a lot of my hardware sucks!

Please & Thanks,
*xMikey*

---

### Post by Sef on 2006-04-28
What sound card to you have?

Here's a link to debugging sound problems.

[https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29]("https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29")

---

### Post by mentallysilent on 2006-04-28
try this:

sudo modprobe snd-au8810 pcifix=1''
alsamixer (unmute and set volume levels)

---

### Post by xMikey on 2006-04-28
[QUOTE=Sef]**What sound card to you have?**

Here's a link to debugging sound problems.

[https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29]("https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29")[/QUOTE]
I have no idea. :confused: My gfx card is an nvidia, so I might have an nvidia soundcard...nForce or something maybe?

lspci -v
```
0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device 4310
        Subsystem: Risq Modular Systems, Inc.: Unknown device 4310
        Flags: bus master, medium devsel, latency 32, IRQ 255
        I/O ports at b800 [disabled] [size=64]
        Capabilities: <available only to root>

```
But that DebuggingSoundProblems link says that thats my soundcard.

[QUOTE=mentallysilent]try this:

sudo modprobe snd-au8810 pcifix=1''
alsamixer (unmute and set volume levels)[/QUOTE]
```
alsamixer: function snd_ctl_open failed for default: No such device

```

In my Sound Preferences under "Default Sound card" the drop down list is blank.  Doesn't reconize it maybe?

---

