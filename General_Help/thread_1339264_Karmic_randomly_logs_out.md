---
title: "Karmic randomly logs out"
date: 2009-11-27
forum: General Help
---

### Post by philbastian on 2009-11-27
Basically I'll be working at my computer and suddenly the screen goes black and then goes to the login screen. This started when I upgraded to Karmic, so I have a feeling that might have *something* to do with it. It tends to happen when I'm using Firefox, but I use Firefox a lot, so I don't know that it's symptomatic. It has happened at least 4-5 times, and seems to be happening more often than at first (it happened last night and this morning).

Here are some logs from this morning's crash--it happened at 9:45 and most of them didn't have much else this morning.

```
auth.log
Nov 27 09:45:44 philb-desktop gdm-session-worker[23673]: pam_unix(gdm:session): session closed for user philb
Nov 27 09:45:44 philb-desktop gnome-keyring-daemon[23713]: dbus failure unregistering from session: Connection is closed
Nov 27 09:45:59 philb-desktop gdm-session-worker[16922]: pam_unix(gdm:session): session opened for user philb by (uid=0)
Nov 27 09:45:59 philb-desktop gdm-session-worker[16922]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

daemon.log
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nov 27 09:45:44 philb-desktop acpid: client 23614[0:0] has disconnected
Nov 27 09:45:44 philb-desktop acpid: client 23614[0:0] has disconnected
Nov 27 09:45:44 philb-desktop acpid: client connected from 16861[0:0]
Nov 27 09:45:44 philb-desktop acpid: client connected from 16861[0:0]

kern.log
(nothing)

messages
Nov 27 09:45:49 philb-desktop bonobo-activation-server (philb-16937): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jnZ3DrJKqr: Connection refused
Nov 27 09:45:59 philb-desktop pulseaudio[17029]: pid.c: Stale PID file, overwriting.

syslog
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Nov 27 09:45:44 philb-desktop console-kit-daemon[950]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nov 27 09:45:44 philb-desktop acpid: client 23614[0:0] has disconnected
Nov 27 09:45:44 philb-desktop acpid: client 23614[0:0] has disconnected
Nov 27 09:45:44 philb-desktop acpid: client connected from 16861[0:0]
Nov 27 09:45:44 philb-desktop acpid: client connected from 16861[0:0]
Nov 27 09:45:49 philb-desktop bonobo-activation-server (philb-16937): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jnZ3DrJKqr: Connection refused
Nov 27 09:45:59 philb-desktop pulseaudio[17029]: pid.c: Stale PID file, overwriting.

user.log
Nov 27 09:45:49 philb-desktop bonobo-activation-server (philb-16937): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jnZ3DrJKqr: Connection refused
Nov 27 09:45:59 philb-desktop pulseaudio[17029]: pid.c: Stale PID file, overwriting.


```

Thanks in advance for your help,
Phil

---

### Post by Vaphell on 2009-11-27
sounds like x crashing down and restarting, usually due to less-than-perfect drivers. what chipset?

---

### Post by philbastian on 2009-11-27
nVidia. And yes, I'm using the proprietary drivers (ver. 185.18.36)

---

### Post by MSDOSNT on 2009-11-27
I have the same issue. It have had it happen while using Firefox or while playing Aisle-riot solitaire. I am using the on-board video (82Q35 Express Integrated Graphics Controller [8086:29B2]) on a P5E-VM DO motherboard. Driver: i915. 

This never happened before the upgrade to Karmic.

---

### Post by dge on 2009-11-28
My experience is exactly the same (interesting AisleRiot Spider Solitaire may have something to do with it).

Also NetworkManager crashed one time, which prompted me to start Bug #480949.  Then I confused the problem reported here with that crash, so I incorrectly described several cases of this problem in that bug report.

The latest occurrence showed this in /var/log/syslog:

[FONT=Courier New]Nov 27 20:23:52 desktop acpid: client 1167[0:0] has disconnected 
Nov 27 20:23:52 desktop acpid: client connected from 3493[0:0] 
Nov 27 20:23:56 desktop bonobo-activation-server (dge-3538): could not associate with desktop session: Failed to connect to socket /tmp/dbus-P35QJC09nj: Connection refused
Nov 27 20:24:14 desktop pulseaudio[3648]: pid.c: Stale PID file, overwriting.
Nov 27 20:24:18 desktop pulseaudio[3648]: module-x11-xsmp.c: X11 session manager not running.
Nov 27 20:24:18 desktop pulseaudio[3648]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.[/FONT]

I have an Intel 4 Series Chipset Integrated Graphics Controller, and the i915 driver, on a Dell 0P301D motherboard in a Vostro220ST.

---

### Post by dge on 2009-11-28
Looks like this is Bug #465317 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/465317](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/465317)

---

### Post by Dave Uggla on 2009-11-29
I can confirm that, at least in my case, that bug is a correct description of the problem. I did not initially know why I was getting logged out, but discovered by using the apport notifier link on my panel that it was a problem with x-org. 

For me, the guaranteed trigger of a crash/re-login was extended use of AisleRiot Solitaire, although there may be a Firefox association too. 

One additional thing which I have noticed is that as I continue to use AisleRiot my memory utilization steadily climbs (primarily the "in use by cache" category). 
If I close AisleRiot and re-open it, the memory allocation returns to normal. If I never let my memory utilization go above about 90% it appears that I can postpone the crash indefinitely.  I cannot think of a legitimate reason for AisleRiot to cause an increase in cache usage, since I don't think it does much if any disk access during play. 

I may find that I need to stop and restart Firefox too, but that has not been necessary yet. 

Dave Uggla

---

### Post by philbastian on 2009-11-29
Hmmmm... That's interesting. I played AisleRoot for about an hour yesterday without any problem whatsoever.

---

### Post by ferrell.charles on 2009-12-02
I am having the same problem.  It's completely random other than the fact that Firefox is open each time it crashes.  I also have an nVidia video card with dual screens.  It generally happens when a page that has flash content is open.  I can't find anything in any of my log files to tell me what may be happening.  It's a pain though.  It happens about once an hour while I'm using Firefox.  I did not have this problem before upgrading to Karmic.  I have a friend that has the same problem.  He uses an intel video card.

---

### Post by philbastian on 2009-12-02
Interestingly, I haven't had any problems since I write the original message. It never was an hourly thing for me, so I can't really tell if something worked, or it just hasn't had a chance to crash.

---

### Post by MSDOSNT on 2009-12-05
Just happened again. No other apps running at the time. I am starting to suspect the mouse as it happens when I am moving the mouse around quickly.

---

### Post by alanjohnsmith on 2009-12-05
these log-outs are happening to me when I'm doing nothing more than trawling through this forum trying to find a solution. Very frustrating.

---

### Post by nigelmouse on 2009-12-09
These are happening to me as well. I'm using an eeepc901 with Intel 945GME and it was fine until a few days ago.

I'd already activated the xorg-edgers launchpad so I was getting newer drivers, but a few days ago an update came out and the random crashing started. I used the ppa-purge app to remove the xorg-edgers packages and revert to the normal karmic packages, but the random X crashes still happen.

the xorg log contains the following:

```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133dbb]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c1395]
2: [0x3bc400]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0xbb8574]
4: /usr/bin/X [0x8181800]
5: /usr/bin/X(ProcPutImage+0x159) [0x808a4c9]
6: /usr/bin/X(Dispatch+0x35f) [0x808d1af]
7: /usr/bin/X(main+0x395) [0x8072515]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x3d3b56]
9: /usr/bin/X [0x80719c1]
Saw signal 7.  Server aborting.
(II) Asus EeePC extra buttons: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) AIGLX: Suspending AIGLX clients for VT switch
 ddxSigGiveUp: Closing log

```

The crashes have all happened when using firefox and opening a new page. 

Could this be a problem in the non-driver part of X given that it's happening on different graphics hardware ?

---

### Post by nigelmouse on 2009-12-10
I've restored my system from a backup I made before enabling the xorg-edgers ppa. I've run the system update and X hasn't crashed all day. 

I think somehow adding the xorg-edgers repository messed something up, and this wasn't fixed by running ppa-purge xorg-edgers.

---

### Post by HonzaPokorny on 2009-12-16
Same issue here. I don't play games though. Firefox, Thunderbird, Filezilla, gedit... 64bit ubuntu. Thanks for any tips.

---

### Post by imwithid on 2009-12-21
It has happened to me. It was most upsetting as I had rewritten an e-mail already for the second time after Opera had crashed and it was a long one. I thought that the chances of another crash slim. Then this problem happened. Now I'm writing my e-mail on gedit and saving it every sentence. This is ridiculous. All I need now is a hard drive failure to top it off.

I have never used Aisle-riot Solitaire. I do have an Intel G965 Express chipset (DG965OT). A couple things that I have done to the system is to delete my kernel.log and message.log files as they had exploded to over 4GB total (including their .1 backups). That seemed to start after I had removed two old kernel updates through Synaptic.

I really hope Lucid 10.04 will be a good one. So far I've had the worst of compatibilities ever since 8.04. If it wasn't crashing, it was the display or USB transfers. I'd don't want to go back to 7.10.

---

### Post by salambander on 2009-12-24
This is happening to me too, whenever an internet browser (chrome for linux or firefox) is open. It started this morning.

This is a fresh install of Karmic on an Acer Travelmate 2480 with all the default drivers etc - I have changed nothing but the desktop (installed cairo-dock, set up an embedded terminal and enabled some effects in compiz). However, it only started doing this this morning. It has worked perfectly for two weeks.

It's pretty frustrating - has anyone found a sure way to solve this yet?

Some of the bugs that have been referred to mention AisleRiot and other games, but I have not been running them.

I ran this, and it seems to have helped a little. It resets compiz to its default settings. 

```
sudo rm -rf ~/.config/compiz
```

By "helped a little" I mean that it is doing it less often, but it is still doing it. 

It also appears to be linked to Flash, so I just tried to install Flashblock for Firefox. And then it did it again.

---

### Post by collinp on 2009-12-24
There are several already-reported Launchpad bugs that could be linked to this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/486593](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/486593) -- *Random X Crashes*

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/457977](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/457977) -- *gdm random crashes*

---

### Post by nutzxian on 2010-03-04
I'm getting exactly the same issue. For some reason (almost always when I'm typing an email in Gmail over Firefox) Ubuntu simply crashes and the screen immediately goes back to the Login page.

---

### Post by MarcoPau on 2010-03-16
Same here with kubuntu karmic (xorg-edgers and 2.6.32). It happens when I switch to the virtual desktop where I have Kvirc:

Mar 16 10:05:58 pau kdm[1010]: X server for display :0 terminated unexpectedly
Mar 16 10:05:58 pau console-kit-daemon[1057]: GLib-GObject-WARNING: instance with invalid (NULL) class pointer 
Mar 16 10:05:58 pau console-kit-daemon[1057]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Mar 16 10:05:58 pau console-kit-daemon[1057]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Mar 16 10:05:58 pau acpid: client connected from 2632[0:0] 
Mar 16 10:06:00 pau kdm_greet[2648]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: Nessun file o directory

---

### Post by m4lte on 2010-09-19
Spontaneous log out happened in Karmic while using Firefox.

auth.log:
```
Sep 20 00:36:40 malte-laptop gnome-keyring-daemon[1502]: dbus failure unregistering from session: Connection is closed
Sep 20 00:36:40 malte-laptop gnome-keyring-daemon[1502]: dbus failure unregistering from session: Connection is closed
Sep 20 00:36:44 malte-laptop polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.32, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)
Sep 20 00:36:47 malte-laptop gdm-session-worker[1307]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
...
```

---

