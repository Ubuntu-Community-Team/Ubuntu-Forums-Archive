---
title: "Sudden, unexpected log off"
date: 2010-03-06
forum: General Help
---

### Post by djpupeikis on 2010-03-06
Hello,

I am using Ubuntu 10.04.

Sometimes, when I am typing something (etc email) and press ENTER, or SHIFT ENTER, SOMETIMES ubuntu just log off, and when I need to re-login. But unfortunately all my work is lost and I have to work again. 
I can't understant why it is happening, and how I could avoid this nonsense.

Thanks!

---

### Post by ajgreeny on 2010-03-06
10.04 is an alpha OS at the moment and not really for a production environment.  Being alpha you must expect some problems, perhaps due to your particular hardware, or maybe something that the devs are still working on.

With no information on your uses of the system or hardware it is difficult to suggest anything except the normal possibilities in this situation such as power supply, overheating, memory problems, etc etc.

---

### Post by djpupeikis on 2010-03-06
It only happens when I press kind of button configuration related to ENTER. I do not know what exactly, because then I am typing fast It just suddenly log's off. Therefore it can not be power supply, overheating and etc.
I was just wondering, if there is any similar key configuration to such strange log off, but I did not find anything.
Anyway, I will wait a bit, maybe it will be fixed, if nobody have similar experience...

---

### Post by dirtfarmer on 2010-03-07
I am experiencing the same thing. It also happens when I open an application. I have been using 10.04 for a total of 10 or 12 hours now and I have been unexpectedly logged off about 20 times. I haven't been able  to figure out the cause/trigger.

asus p6t, i7920,6gbRam, gtx260gpu,

---

### Post by dirtfarmer on 2010-03-07
Ok, I've looked into this some more. This is a report on the trigger, I haven't found a solution yet.  

After logging on to Gnome desktop for the first time after system boot, it kills xserver  the first time the enter/return button is pressed. This happens whether you have any applications running or not.  You then have to log back in , and the enter/return key functions properly. 

I am a new user and don't know how to report this as an official bug. I forgot to mention that I am running 64bit version of 10.04. And it is fully updated at the time of this posting.

---

### Post by djpupeikis on 2010-03-08
Gosh! That really annoys me!
I am just starting to think to get back to illegal Windows...

Video card- NVIDIA GF 7300 GT.
RAM- 1,5GB
CPU- Amd Athlon 1800..
I am new to ubuntu.

---

### Post by bleedingpowers on 2010-03-23
I must confirm the same bug existing on Ubuntu 9.10 (Karmic Koala)... Unexpected/Sudden user account logout / logoff. Happens by the combination of some keystrokes (I don't know which).

If I immediately look/view the Log (System Log Viewer), I see messages related to pulseaudio, like this one:

```
pulseaudio[30099]: pid.c: Stale PID file, overwriting.
```

However, I'm not sure if I'm on the right track or just misleading everyone.

Let's keep on digging for a solution. We can't permit users switching back to MS hell!

---

### Post by blueairmaster on 2010-04-08
*I just had a sudden logoff with "Apr  8 07:59:33 V7250 pulseaudio[2266]: pid.c: Stale PID file, overwriting." in my user.log*

Was running Firefox, gedit, and System Monitor. Had been logged on for about 10 minutes.

---

### Post by blueairmaster on 2010-04-08
I am running 9.10. Yesterday I removed Windows Vista and did a fresh install of Ubuntu 9.1 only. I had been dual booting for the previous 5 months or so and never had a sudden logoff.

---

### Post by xhalarin on 2010-04-08
I have the issue of auto-logout in 9.10 although it's no longer big a problem for me.  It seems to occur the first time I boot into a hardware configuration (possibly related to the Nvidia driver).  If I reboot right away after booting up the first time on the config, the auto-logout doesn't happen again on that set of hardware.

---

### Post by 3rdalbum on 2010-04-08
Try and narrow down what might be causing it - for instance, if you can trigger it at the login screen, then it's obviously not Gnome (because Gnome isn't running yet), but it might be gdm or Xorg. Or, if KDE doesn't have the problem, then it's probably a Gnome problem.

Once you've figured out an approximate package to report it against (for instance, against "gdm" or against "gnome"), then trigger the problem, log in again and type this into a terminal:

```
apport-bug <packagename>
```

For instance, "apport-bug gdm".

Apport will collect as much information as possible about the current state of your system, and open up a web browser at the Launchpad website to let you submit a bug report. (the information will be submitted along with your bug). At the first step, you have to use a couple of words to describe the problem, and then it'll ask you whether your problem is the same as some other, previously-reported bugs. If it is, then don't open a new bug report (unless the older bug is described as "Fix released" or is stale - use your own judgement).

And yeah, provide as much information as possible. Make sure you put in the following section:

[I]Steps I took to trigger this problem:

1. Log in
2. Open Gedit
3. Type some text
4. Press Enter

What I expected to happen:

I expected a new line to appear in Gedit

What actually happened:

X server quit and was dumped back to the login screen.[/I]

That's just an example, of course. But it's very good bug reporting practice to include a section like that, laid out like that too.

When you're done, you'll be informed by e-mail every time somebody comments on it, and every time its status gets changed.

---

### Post by tomcheng76 on 2010-04-16
i get the same message in /var/log/message when lucid beta 2 auto logoff.
pulseaudio[2341]: pid.c: Stale PID file, overwriting.
bonobo-activation-server (x-6917): could not associate with desktop session: Failed to connect to socket /tmp/dbus-iXImIJ1Po0: Connection refused

And i am using nvidia too. 8600GT with 195.36.15 (nvidia-current).

I am unable to trigger the problem (few days happen once)

---

### Post by happyhamster on 2010-04-16
> 
pulseaudio[2341]: pid.c: Stale PID file, overwriting.


That likely means that in order for pulseaudio to successfully (re)start, it has to overwrite some "stale" files that remained when something (X, gdm, ...) crashed sometime earlier. In other words: the crash very likely happened before that message, and the message itself only says that pulse encountered some problem and took care of it (it doesn't say anything about the cause of that problem). That's how I understand it anyway.

For lucid, there was an enter-key = crash problem related to plymouth, but that one appears to be fixed. Info:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532047](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532047)
(See also the numerous duplicate reports).

---

### Post by greggus on 2010-05-16
The same problem here.

Syslog shows:

May 16 13:23:29 z-desktop kernel: [   20.476566] agpgart-via 0000:00:00.0: AGP 3.5 bridge
May 16 13:23:29 z-desktop kernel: [   20.476593] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
May 16 13:23:29 z-desktop kernel: [   20.476659] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode

I think it can be a reason. X server reloads and login screen shows up.
Any ideas?

---

### Post by Stijndg on 2010-06-01
Still having this problem with my Lucid Lynx Setup, it's getting very annoying. Anyone been able to short-circuit this problem?

---

### Post by Zyggurat on 2010-06-12
Having the same problem on my laptop.  Didn't happen on any previous release prior to Lucid.  Seems to happen at least 50% of the time I log on now.  Usually after doing something at random about 15 to 30 minutes after I log on.

---

### Post by opus1 on 2010-06-12
I too can confirm this bug on a Dell Latitude C610 laptop.  I have had it happen 3 times now and is the straw that broke the camels back... on top of the other problems I've had with Lucid, I'm throwing in the towel and going back to Hardy.

---

### Post by Dignitos on 2010-06-20
I have the same problem, sometimes once a day, sometimes several times.

Is there really no way to avoid this? (apart from stop pressing enter, which is not really realistic)

The problem appears in Chrome, Pidgin, any other application, and sometimes after several hours of system usage. I find no pattern apart from the fact that it is always triggered by pressing enter.

---

### Post by anivegmin on 2010-08-27
Same problem here - seems to be when typing fast (not sure if it is something to do with a hot key combination) I hit enter and the session logs out. Can't figure it out. Very annoying because you lose everything.

---

### Post by spegru on 2010-08-29
I get exactly the same thing in Linux Mint 9, which of course is based on Ubuntu 10.04.
I notice that it always goes exactly as I press a key, but I am sure it is not a key combination.
Looks like an X11 crash to me. As far as I know, X11 also includes the keyboard as well as the screen
I got the same OS on a few different machines, but only one has the problem

I havnt had a chance to look at syslog yet....

---

### Post by spegru on 2010-09-13
It's still being a problem.
I finally got round to looking in syslog

Here are parts that seem to be relevant

Sep 13 12:38:52 stephen-desktop gnome-session[1728]: WARNING: Detected that screensaver has left the bus
Sep 13 12:38:52 stephen-desktop gdm-simple-slave[3182]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 13 12:38:53 stephen-desktop acpid: client 1289[0:0] has disconnected
Sep 13 12:38:53 stephen-desktop acpid: client connected from 3187[0:0]
Sep 13 12:38:53 stephen-desktop acpid: 1 client rule loaded
Sep 13 12:38:53 stephen-desktop pulseaudio[3184]: pid.c: Stale PID file, overwriting.
Sep 13 12:38:53 stephen-desktop pulseaudio[3184]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-7FquIIs7EY: Connection refused
Sep 13 12:38:53 stephen-desktop pulseaudio[3192]: pid.c: Daemon already running.
Sep 13 12:38:54 stephen-desktop acpid: client connected from 3187[0:0]
Sep 13 12:38:54 stephen-desktop acpid: 1 client rule loaded
Sep 13 12:38:54 stephen-desktop gdm-session-worker[3227]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 13 12:38:54 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3231 of process 3231 (n/a) owned by '114' high priority at nice level -11.
Sep 13 12:38:54 stephen-desktop rtkit-daemon[1551]: Supervising 1 threads of 1 processes of 2 users.
Sep 13 12:38:54 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3232 of process 3231 (n/a) owned by '114' RT at priority 5.
Sep 13 12:38:54 stephen-desktop rtkit-daemon[1551]: Supervising 2 threads of 1 processes of 2 users.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3234 of process 3231 (n/a) owned by '114' RT at priority 5.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Supervising 3 threads of 1 processes of 2 users.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3235 of process 3231 (n/a) owned by '114' RT at priority 5.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Supervising 4 threads of 1 processes of 2 users.
Sep 13 12:38:55 stephen-desktop gdm-simple-greeter[3226]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3243 of process 3231 (n/a) owned by '114' RT at priority 5.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Supervising 5 threads of 1 processes of 2 users.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Sucessfully made thread 3244 of process 3231 (n/a) owned by '114' RT at priority 5.
Sep 13 12:38:55 stephen-desktop rtkit-daemon[1551]: Supervising 6 threads of 1 processes of 2 users.
Sep 13 12:38:58 stephen-desktop gdm-session-worker[3227]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep 13 12:39:00 stephen-desktop gdm-session-worker[3227]: pam_sm_authenticate: Called
Sep 13 12:39:00 stephen-desktop gdm-session-worker[3227]: pam_sm_authenticate: username = [stephen]
Sep 13 12:39:01 stephen-desktop gnome-session[3267]: EggSMClient-WARNING: Desktop file '/home/stephen/.config/autostart/skype.desktop' has malformed Icon key 'skype.png'(should not include extension)
Sep 13 12:39:03 stephen-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Sep 13 12:39:03 stephen-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Sep 13 12:39:06 stephen-desktop init: tty2 main process ended, respawning

The last part about respawning is presumably the bit where the session closes suddenly and the login screen reappears.
Any ideas?

---

### Post by artemgab on 2010-09-18
I have this problem with my 10.04. These unexpected logoffs happened before, but then for some time Ubuntu behaved itself and I thought the bug was gone.
Today I was watching a movie when this thing happened. Maybe the list of running apps could be of some use. I was running: Smplayer, DoubleCommander, Pidgin, Mozilla Firefox and I'm not sure about: Wine XMPlay.exe, amule. I am pretty sure I had not hit <Enter> when logoff happend. I suspect that it's Pidgin and SMPlayer, who were fighting for a soundcard (imagine: instant message received by pidgin causes sound notification, interference with smplayer - bang - thus we have arbitrariness). Pidgin uses ALSA for sound, SMPlayer used pulse. Now I temporary switched SMPlayer to ALSA (0.0 HDA NVidia) to see if it helps or is it a sound issue at all.
Logoff happened on tty7, then login screen appeared (?X were restarting?) on tty8.

By the way here is my syslog:
```
Sep 18 23:14:59 joybox pulseaudio[1477]: ratelimit.c: 73 events suppressed
Sep 18 23:17:01 joybox CRON[2683]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 18 23:20:01 joybox pulseaudio[1477]: ratelimit.c: 74 events suppressed
Sep 18 23:20:59 joybox pulseaudio[1477]: ratelimit.c: 79 events suppressed
Sep 18 23:21:21 joybox pulseaudio[1477]: ratelimit.c: 76 events suppressed
Sep 18 23:51:48 joybox acpid: client 911[0:0] has disconnected
Sep 18 23:51:48 joybox acpid: client connected from 2844[0:0]
Sep 18 23:51:48 joybox acpid: 1 client rule loaded
Sep 18 23:51:49 joybox acpid: client connected from 2844[0:0]
Sep 18 23:51:49 joybox acpid: 1 client rule loaded
Sep 18 23:51:53 joybox bonobo-activation-server (joyuser-2879): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HRJycpn4la: Connection refused
Sep 18 23:51:54 joybox gdm-simple-greeter[2881]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep 18 23:51:55 joybox gdm-simple-greeter[2881]: WARNING: Unable to lookup user name gazer: Success
Sep 18 23:51:56 joybox gdm-simple-greeter[2881]: WARNING: Unable to lookup user name gaz: Success
Sep 18 23:52:00 joybox gdm-session-worker[2885]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep 18 23:52:06 joybox rtkit-daemon[1479]: Sucessfully made thread 2977 of process 2977 (n/a) owned by '1000' high priority at nice level -11.
Sep 18 23:52:06 joybox rtkit-daemon[1479]: Supervising 1 threads of 1 processes of 1 users.
Sep 18 23:52:06 joybox pulseaudio[2977]: pid.c: Stale PID file, overwriting.
```

---

### Post by nickflyer on 2010-09-26
Sep 26 20:17:02 nickflyer-desktop CRON[22772]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 26 20:17:55 nickflyer-desktop kernel: [40091.744131] radeon 0000:01:05.0: r600_cs_track_check:280 mask 0xFFFFFFFF | 0xFFFFFFFF no cb for 0
Sep 26 20:17:55 nickflyer-desktop kernel: [40091.744135] radeon 0000:01:05.0: r600_packet3_check:1108 invalid cmd stream 38
Sep 26 20:17:55 nickflyer-desktop kernel: [40091.744137] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
**Sep 26 20:32:17** nickflyer-desktop kernel: [40954.110753] indicator-sound[20159]: segfault at 18 ip b71028fa sp bfad5894 error 4 in libxcb.so.1.1.0[b70f6000+18000]
Sep 26 20:32:18 nickflyer-desktop NetworkManager[1422]: <error> [1285551138.290038] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep 26 20:32:20 nickflyer-desktop gdm-simple-slave[22984]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 26 20:32:21 nickflyer-desktop acpid: client 19781[0:0] has disconnected
Sep 26 20:32:21 nickflyer-desktop acpid: client connected from 22986[0:0]
Sep 26 20:32:21 nickflyer-desktop acpid: 1 client rule loaded
Sep 26 20:32:23 nickflyer-desktop NetworkManager[1422]: <error> [1285551143.378048] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Sep 26 20:32:26 nickflyer-desktop gdm-session-worker[23027]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 26 20:32:26 nickflyer-desktop rtkit-daemon[1967]: Successfully made thread 23033 of process 23033 (n/a) owned by '114' high priority at nice level -11.
Sep 26 20:32:26 nickflyer-desktop rtkit-daemon[1967]: Supervising 1 threads of 1 processes of 1 users.
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Successfully made thread 23036 of process 23033 (n/a) owned by '114' RT at priority 5.
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Supervising 2 threads of 1 processes of 1 users.
Sep 26 20:32:27 nickflyer-desktop gdm-simple-greeter[23025]: Gtk-WARNING: /build/buildd/gtk+2.0-2.21.7/gtk/gtkwidget.c:5678: widget not within a GtkWindow
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Successfully made thread 23038 of process 23033 (n/a) owned by '114' RT at priority 5.
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Supervising 3 threads of 1 processes of 1 users.
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Successfully made thread 23039 of process 23033 (n/a) owned by '114' RT at priority 5.
Sep 26 20:32:27 nickflyer-desktop rtkit-daemon[1967]: Supervising 4 threads of 1 processes of 1 users.
Sep 26 20:32:28 nickflyer-desktop gdm-simple-greeter[23025]: WARNING: Unable to lookup user name nickflye: Success
Sep 26 20:32:31 nickflyer-desktop gdm-session-worker[23027]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep 26 20:32:34 nickflyer-desktop gdm-session-worker[23027]: pam_sm_authenticate: Called
Sep 26 20:32:34 nickflyer-desktop gdm-session-worker[23027]: pam_sm_authenticate: username = [nickflyer]
Sep 26 20:32:34 nickflyer-desktop gdm-session-worker[23048]: Passphrase file wrapped

I think the log-out started at the time in BOLD... I watched the computer idle from my bed and jumped up to catch this exactly when it logged out.... so, near the end is me logging back in.

---

### Post by nickflyer on 2010-09-27
it looks like my issue may have been resolved
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/640127)

---

### Post by crashflow on 2010-10-19
At my system, the unexpected logoffs started to occur again.

At least this is better than the random freezing I have gotten used to over the past 2 years (which is now gone).

crashflow

---

### Post by SchneiderIS on 2011-01-03
I am getting this same issue with a 10.10 install.  Did you find a solution for it?  Is it the Pulse Audio still?

It looks like the referenced bug submission did not resolve the issue.

---

### Post by psycho2base on 2011-01-22
After update i have this too in 10.10 for now i got it when i'm browsing with firefox... Any ideas how to fix?

---

### Post by SchneiderIS on 2011-01-23
Under myth I bad a developer tell 
me to switch to slim node under vdpau.  The fact that not everyone is running myth and is still getting the same result tells me that we realy don't know the cause.  The problem resides with x server and commuting on the bug or submitting the same bug may be the only way to get a resolution.

---

### Post by CoolDreamZ on 2011-02-18
I have a similar issue and have logged this bug:
[URL="https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/709642"]
https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/709642[/URL]

---

### Post by alfonso78 on 2011-03-15
Hi,

I have the same problem with Ubuntu 10.10.

Normally it happened randomly, but I found a way to reproduce the bug.

I'm not in front of the PC so I can't give precise instructions, but if I go into audio settings and change the audio volume (not master volume) while a flash video is playing on the browser it crashes 100% of times.

Can you try if this happens as well for you? having a clear way to reproduce the bug might help us solve the problem.

Let me know if you need more detailed explanation of how I reproduce the bug.

Since it's related to the video, I will share more info on my setup, maybe we discover we have similar systems!

I have a ZOTAC H55-ITX WiFi (H55ITX-C-E variant, with USB 3.0), intel i3 550, my screen is connected via HDMI and I changed the settings to send audio via the HDMI.
I also connected a wireless speaker via USB.

Let's see if we have some configuration in common.

As soon as I have time I'll also reinstall the system and try to use chrome instead of firefox (to avoid the external flash plugin).

alfonso

---

