---
title: "bonobo-activation-sever crash"
date: 2010-05-03
forum: General Help
---

### Post by Sevy on 2010-05-03
Two of my three pcs crash running Lucid and here is whats in messages for my main pc


May  3 12:49:55 sevy-desktop kernel: [   19.937454] usbcore: registered new interface driver oss_usb
May  3 13:16:19 sevy-desktop bonobo-activation-server (sevy-2131): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HBmcGYsrRq: Connection refused
May  3 13:19:10 sevy-desktop kernel: Kernel logging (proc) stopped.
May  3 13:19:10 sevy-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="602" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  3 13:19:45 sevy-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  3 13:19:45 sevy-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="596" x-info="http://www.rsyslog.com"] (re)start
May  3 13:19:45 sevy-desktop rsyslogd: rsyslogd's groupid changed to 102
May  3 13:19:45 sevy-desktop rsyslogd: rsyslogd's userid changed to 101
May  3 13:19:45 sevy-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset

Any ideas?

---

### Post by dino99 on 2010-05-03
server down ? something unplugged ?

---

### Post by Sevy on 2010-05-03
Everything is plugged in

---

### Post by Sevy on 2010-05-03
bump:(

---

### Post by Sevy on 2010-05-04
luckily I cloned all three of my pcs running karmic using clonezilla so Im thinking of going back.
Im finding it hard to get any info on bonobo

---

### Post by Sevy on 2010-05-05
Good news!
On one pc I went back to Karmic and then ran the upgrade again and so far so good,I dont know what changed.
On my main pc I changed ubuntu desktop to xubuntu desktop and again it seems ok
:p

---

### Post by Sevy on 2010-05-05
I reinstalled Lucid but for it to only crash again after 2 hours

May  5 21:58:38 sevy-desktop bonobo-activation-server (sevy-1842): could not associate with desktop session: Failed to connect to socket /tmp/dbus-p3bYG71313: Connection refused

I dont really want to use Xubuntu but I dont know what else to try

????

---

### Post by robinmurray on 2010-05-06
I also have this issue. 
here is a snippet from my logs.

```
May  6 20:24:48 office bonobo-activation-server (robin-1948): could not associate with desktop session: Failed to connect to socket /tmp/dbus-KKadG08qtf: Connection refused
May  6 20:24:50 office kernel: Kernel logging (proc) stopped.

```

is this linked in any way with pulse audio?

```

May  5 22:19:22 office pulseaudio[1678]: pid.c: Stale PID file, overwriting.
May  5 22:19:24 office pulseaudio[1678]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-IOdt9M6l0i: Connection refused
May  5 22:19:25 office bonobo-activation-server (robin-1687): could not associate with desktop session: Failed to connect to socket /tmp/dbus-IOdt9M6l0i: Connection refused
May  5 22:19:28 office kernel: Kernel logging (proc) stopped.

```

Any help greatly appreciated.

---

### Post by Sevy on 2010-05-06
When I select the GL slideshow screensaver I get the same crash,a quick purple splash screen with Ubuntu scrambled and then a black screen with white vertical lines that flash on and off.
It also gives me the same error in the logs.
I will try disabling the screensaver

---

### Post by chandearriba on 2010-05-11
I'm sorry to resurrect this thread, but I think I have the same issue here, with bonobo-activation-server being unable to associate with desktop bla, bla, following some «Stale PID file, overwriting» from pulse audio, exactly as in the robinmurray's case. Has anyone found some sort of workaround for this? Could it be a hardware-related issue?

Just in case: 
-Computer-
Processor        : 2x Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
Memory        : 3078MB (602MB used)
Operating System        : Ubuntu 10.04 LTS
User Name        : xxxxxxx
Date/Time        : mar 11 may 2010 14:12:07 CEST
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Mesa DRI Intel(R) 965Q GEM 20091221 2009Q4 x86/MMX/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Sleep Button
 Power Button
 Macintosh mouse button emulation
 Unicomp  Endura Keyboard
 Logitech USB Trackball
 HDA Digital PCBeep
 HDA Intel Line In at Ext Rear Jack
 HDA Intel Mic at Ext Front Jack
 HDA Intel Mic at Ext Rear Jack
 HDA Intel Mic at Ext Rear Jack
 HDA Intel Line In at Ext Rear Jack
 HDA Intel Line Out at Ext Rear Jack
 HDA Intel HP Out at Ext Front Jack
-Printers-
No printers found
-SCSI Disks-
ATA ST3500320AS
HL-DT-ST DVDRAM GSA-H12N
HL-DT-ST DVD-ROM GDR8164B

---

### Post by FoH on 2010-05-12
I'm having a similar problem. Once in a while, I get logged out of the current session, or rather thrown out to the GDM screen. When I log on again and run the users command in a terminal it shows that my user is logged in twice:
```
martin@martin-desktop:~$ users
martin martin
```

This has occurred on Ubuntu 9.10 also (I'm running Lucid now, fresh install, x64), particularly when launching PS3 Media Server (Java-based) but only like 1/30 of the times. This time, I launched Virtualbox (Lucid Server instance) and went away for a couple of minutes, and when I got back I was at the GDM screen.

Syslog has this to say:
```
May 13 02:44:41 martin-desktop kernel: [113966.526194] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
May 13 02:50:23 martin-desktop kernel: [114308.500033] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 13 02:50:23 martin-desktop kernel: [114308.500042] render error detected, EIR: 0x00000000
May 13 02:50:23 martin-desktop kernel: [114308.500063] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 5777904 at 5777903)
May 13 02:50:24 martin-desktop kernel: [114309.260026] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 13 02:50:24 martin-desktop kernel: [114309.260032] render error detected, EIR: 0x00000000
May 13 02:50:24 martin-desktop kernel: [114309.261468] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 5777906 at 5777903)
May 13 02:50:25 martin-desktop acpid: client 1213[0:0] has disconnected
May 13 02:50:25 martin-desktop acpid: client connected from 15440[0:0]
May 13 02:50:25 martin-desktop acpid: 1 client rule loaded
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 15648 of process 15648 (n/a) owned by '114' high priority at nice level -11.
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Supervising 1 threads of 1 processes of 1 users.
May 13 02:50:28 martin-desktop gdm-simple-greeter[15631]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 15683 of process 15648 (n/a) owned by '114' RT at priority 5.
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Supervising 2 threads of 1 processes of 1 users.
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 15688 of process 15648 (n/a) owned by '114' RT at priority 5.
May 13 02:50:28 martin-desktop rtkit-daemon[1557]: Supervising 3 threads of 1 processes of 1 users.
May 13 02:50:29 martin-desktop bonobo-activation-server (martin-15775): could not associate with desktop session: Failed to connect to socket /tmp/dbus-6ecRQ8SNSn: Connection refused
May 13 02:50:44 martin-desktop gdm-session-worker[15637]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 13 02:50:46 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 17368 of process 17368 (n/a) owned by '1000' high priority at nice level -11.
May 13 02:50:46 martin-desktop rtkit-daemon[1557]: Supervising 4 threads of 2 processes of 2 users.
May 13 02:50:46 martin-desktop pulseaudio[17368]: pid.c: Stale PID file, overwriting.
May 13 02:50:47 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 17403 of process 17368 (n/a) owned by '1000' RT at priority 5.
May 13 02:50:47 martin-desktop rtkit-daemon[1557]: Supervising 5 threads of 2 processes of 2 users.
May 13 02:50:47 martin-desktop rtkit-daemon[1557]: Sucessfully made thread 17408 of process 17368 (n/a) owned by '1000' RT at priority 5.
May 13 02:50:47 martin-desktop rtkit-daemon[1557]: Supervising 6 threads of 2 processes of 2 users.
```

messages.log says:
```
May 13 02:44:41 martin-desktop kernel: [113966.526194] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
May 13 02:50:29 martin-desktop bonobo-activation-server (martin-15775): could not associate with desktop session: Failed to connect to socket /tmp/dbus-6ecRQ8SNSn: Connection refused
May 13 02:50:46 martin-desktop pulseaudio[17368]: pid.c: Stale PID file, overwriting.
```

Is there a way to connect to an already running session? It doesn't show up on the GDM screen.

---

### Post by Sevy on 2010-06-21
Ive found one way round this.
I experience the bonobo crash when using kernel 2.6.32.22 and previous 2.6.32.**(Havent tested them all)
No crashes were experienced when using 2.6.31.** but had problems trying to install oss.
So I have settled on using the rt kernel in synaptic for now.

---

### Post by SteveDee on 2010-06-26
I was on the verge of dumping Lucid (it could still happen) because I have a similar problem where the screen blanks (sometimes it strobes between blank, and black with some white text) on several of our computers.

The worst example is my Dell Inspiron 500m which has the dreaded Intel 82852/855GM graphics, and I needed to re-enable KMS as described here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) in order to run the LiveCD and install.
On this laptop I can crash it (resulting in the "bonobo-activation-server" message appearing in the log) by a number of means including:-
 - running the video test as part of System > Administration > System Testing
 - video test via gstreamer-properties
 - trying to run a *.avi or *.mp4 video

When it does crash, I can't vnc in from a remote pc, so its clearly more than just a display issue.

I also went back to: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and tried "Workaround F" which is supposed to work flawlessly with my hardware...it didn't.

> **Sevy said:**
> Ive found one way round this.
I experience the bonobo crash when using kernel 2.6.32.22 and previous 2.6.32.**(Havent tested them all)
No crashes were experienced when using 2.6.31.** but had problems trying to install oss.
So I have settled on using the rt kernel in synaptic for now.

So then I tried the rt kernel, which boots with the message: "mount: mounting none on /dev failed: No such device"
Initially I thought this was a show-stopper. But this morning I tried again and found this message clears after about 20s and continues to boot.
I can now run videos and the gstreamer-properties video test OK. The video part of System Testing does not work, but at least it does not crash....thanks very much Sevy, you have saved Lucid from extermination

Now I just need to get my collection of Compaq D510s working. This will be more difficult to test as I don't have a reliable way to crash them.

For me, Lucid has been a very bad experience. I'd like to see the developers burn a new Lucid iso with a user configuration menu added at startup, so if the default configuration does not run the LiveCD, the user has the option of selecting a few alternatives.

I completely switched to Ubuntu in 2008 with 8.04, a distro that lived up to its name "Hardy" because all the basics worked. Since then I have experienced problems with each new release, but Lucid is in a (low) class of its own.

---

### Post by Sevy on 2010-06-27
Its coming up to a week with no crashes:p but the occasional freeze about once every two days.
I have also enabled KMS and will soon try the other options in
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")
I have the 82845G chip on an HP D51C

---

### Post by SteveDee on 2010-06-28
Sevy, I'll be interested to hear if you can crack this, as my Compaq D510 probably uses the same chip. Running lspci reveals:-

```

Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

I'm using the rt kernel and have included some of the recommended fixes by adding an xorg.conf that looks like this:-

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
	Option		"AccelMethod" "UXA"
	option		"DRI"	"off"
	VideoRam	130560
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

This has allowed me to run Google Sketchup under Wine, which previously crashed the system everytime.

The computer will now run for hours OK, but then you do something random and the damn thing will blank.

Its also booted a couple of times since making these mods, and failed to find the mouse! (disconnecting then reconnecting the mouse fixes this).

---

### Post by SteveDee on 2010-09-16
I've continued to experience crashes during the last couple of months and I suspect some recent software updates may have made this problem worse.

A couple of workarounds I have discovered (in addition to #13 & #15 above) may be of interest to others:-

1. Videos crash the system when played in the default app Movie Player. I installed SMPlayer a while back and set the Video Output Driver option to X11 (slow). This seems to play video and never crash, but can be a bit jerky when running full screen.

2. Crashes in FireFox when playing video content led me to start changing the FireFox options in Edit > Preferences > Applications so that each video file type would use SMPlayer. But this was a tedious operation, so I went back to gstreamer-properties and set the video Default Output Plugin to: X Window System (no Xv). This now seems to allow me to use default application settings in FireFox, including Movie Player.

---

### Post by pterion on 2011-11-28
Just happened to me to using Lucid. Suddenly, I was logged out and thrown back to GDM.

```
Nov 28 10:42:13 ares bonobo-activation-server (dtka-2555): could not associate with desktop session: Failed to connect to socket /tmp/dbus-iA6Q9vMyGU: Connection refused
```

```
$ uname -r
2.6.32-35-generic
```

Before I was away from the PC for some time and when coming back surprisingly found it being turned off.

---

