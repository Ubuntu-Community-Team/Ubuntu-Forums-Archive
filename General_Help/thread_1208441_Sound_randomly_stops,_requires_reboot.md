---
title: "Sound randomly stops, requires reboot"
date: 2009-07-09
forum: General Help
---

### Post by blueridgedog on 2009-07-09
I posted this originally in the multimedia group, but received little interest.  

My 8.10 system has excellent sound quality and plays sound fine in every way, except that it periodically stops working (usually when I am not even using the system...such as in the middle of the night).  This is easily fixed with a reboot, but I am tired of it and would really like to find a fix or a way to restart whatever process has stalled.

lspci reveals:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

I just brought up my Pandora tab to click play and realized that after 4 days of great sound, now I need a reboot, and I have too many things running now to restart at the moment.  Help me solve this please.

---

### Post by danwood76 on 2009-07-09
Next time the audio stops run the two following commands and see if it comes back:
```

pulseaudio -k
pulseaudio -D

```
This will simply restart the pulseaudio sound server, if this restarts the audio then you have narrowed it down to a pulse issue.

---

### Post by blueridgedog on 2009-07-09
> **danwood76 said:**
> Next time the audio stops run the two following commands and see if it comes back:
```

pulseaudio -k
pulseaudio -D

```
This will simply restart the pulseaudio sound server, if this restarts the audio then you have narrowed it down to a pulse issue.

Odd results:

Running as root gave the following:

```
root@Ripstop:/home/# /usr/bin/pulseaudio -k
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.
root@Ripstop:/home/# /usr/bin/pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: This program is not intended to be run as root (unless --system is specified).
```

Running as "me" gave the following:

```
~$ pulseaudio -k
W: ltdl-bind-now.c: Failed to find original dlopen loader.
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.
```

---

### Post by wpshooter on 2009-07-09
I think I would first run a check of the file system.

And if that did not work I would start to look at hardware because, hmmmmmmm, works great with installed software and then all of a sudden just stops.  I think I would particularily run memtest, I would also monitor temperatures to make sure that they were not getting to high, then I would consider running diagnostics on all system hardware particularily hard drive and processor.

But my bet is either first memory problem, followed by temperature problem.

---

### Post by blueridgedog on 2009-07-09
I have new information.

Killing pulseaudio and restarting it worked, but it was reluctant to go:
```

:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6656 ?        Ssl    8:03 /usr/bin/pulseaudio -D --log-target=syslog
 6659 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
:~$ sudo killall pulseaudio
:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6656 ?        Ssl    8:03 /usr/bin/pulseaudio -D --log-target=syslog
 6659 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
:~$ kill -9 6656
```

After starting it, sound returns:

```
:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10407 ?        Ssl    0:00 pulseaudio -D
10410 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
10412 pts/0    R+     0:00 grep pulse
```

As far as temps, I keep conky up and my temps are pretty low (I have an obsession with quite cool systems and my current build has a quad core chip with a noctua cooler coupled with 4 noctua case fans).

I will run memtest, but the system has no other issues an is frequently under heavy use encoding audio and video.

---

### Post by wpshooter on 2009-07-09
> **blueridgedog said:**
> I have new information.

Killing pulseaudio and restarting it worked, but it was reluctant to go:
```

:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6656 ?        Ssl    8:03 /usr/bin/pulseaudio -D --log-target=syslog
 6659 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
:~$ sudo killall pulseaudio
:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 6656 ?        Ssl    8:03 /usr/bin/pulseaudio -D --log-target=syslog
 6659 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
:~$ kill -9 6656
```

After starting it, sound returns:

```
:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
:~$ ps ax | grep pulse
 6652 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10407 ?        Ssl    0:00 pulseaudio -D
10410 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
10412 pts/0    R+     0:00 grep pulse
```

As far as temps, I keep conky up and my temps are pretty low (I have an obsession with quite cool systems and my current build has a quad core chip with a noctua cooler coupled with 4 noctua case fans).

I will run memtest, but the system has no other issues an is frequently under heavy use encoding audio and video.

I think I would try reseating the memory modules.  Might want to try switching slots while you are at it.

---

### Post by danwood76 on 2009-07-10
> **blueridgedog said:**
> I have new information.

Killing pulseaudio and restarting it worked, but it was reluctant to go:

........

I will run memtest, but the system has no other issues an is frequently under heavy use encoding audio and video.

This most probably is an issue with pulseaudio, sometimes pulse crashes or its thread locks waiting for something. You will have to look at the software you use and see if any of it is left running.

The way to debug pulseaudio is to start it up in verbose mode and have  alook what its doing when it crashes.
This involves leaving a terminal open with the command 'pulseaudio -vvv' once you have killed pulse. (it will obviously function normally whilst in verbose mode)

To force pulse to quit you can use the following:
```

killall -9 pulseaudio

```

Memtest will pass with flying colours and you will have wasted a few hours.
It doesn't look like a memory issue as you would experiance omore issues than just pulseaudio crashing.

---

### Post by blueridgedog on 2009-07-10
I am running pulseaudio in a terminal now.

This is progress.  First, I have a way to restore sound now without a reboot and I have a handle on where the issue resides.

---

### Post by blueridgedog on 2009-07-11
After returning from a overnight business trip, the terminal in which I had run pulseaudio was full of lines with:

```
W: protocol-native.c: Failed to push data into queue
```

A search on this error reveals a few bugs that in theory were addressed in the latest release and several posts about how to remove pulse and use another tool.  

My current version is 0.9.10.  I see that 0.9.15 is out.  Is there a preferred way to upgrade mine?

It seems I simply need to add this to my repos:

[https://launchpad.net/~next-media/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=intrepid](https://launchpad.net/~next-media/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=intrepid)

---

### Post by danwood76 on 2009-07-12
Yes add that ppa or build it from source.
The ppa would be a lot easier!

---

### Post by blueridgedog on 2009-07-12
Well, I added the ppa and upgraded the 100 or so items (it seems) that the repository had.  I will let it run for a day or so and see if it solves the problem.

---

### Post by blueridgedog on 2009-07-16
Since updating pulseaudio via the backport as listed, the issue has not returned.

---

