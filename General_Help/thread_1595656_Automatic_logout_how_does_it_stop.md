---
title: "Automatic logout: how does it stop?"
date: 2010-10-13
forum: General Help
---

### Post by jcoglan on 2010-10-13
So if I leave my Ubuntu desktop (10.04) alone for a while (e.g. if I'm in a meeting) it logs me out and I lose all the work and apps I had open. Is this a bug, or did I misconfigure something? How do I stop it happening?

---

### Post by jcoglan on 2011-03-10
Bump. This is incredibly annoying and I keeping losing work because of it.

---

### Post by lithopsian on 2011-03-10
Power saving?  Trying to hibernate but not doing it very well?

---

### Post by jcoglan on 2011-03-10
I can't see anything in my power saving settings that relates to this. What kind of thing could I check for to get more information?

---

### Post by Cheesehead on 2011-03-10
'Automatically logging out' is usually X (the software that controls the screen) crashing. The system automatically restarts X when it crashes, which restarts Gnome...which is why you wind up at the login screen, which is part of Gnome's restart. X crashes used to be much more common a few years ago, but are now quite rare as most of those bugs have been fixed.

You haven't provided enough information yet.

Does this *only* happen when the system is left idle? For how long? Has this ever happened while the system was not idle? If so, what were you doing?

Does this happen only when certain software is running? Have you installed any unsupported software (like PPAs) around the time this issue began?

Open your power manager - how long is the delay until sleep/suspend?

Open the file /var/log/syslog and look for a time near one of the restarts (there should be a lot of activity around that time). Look for an error or warning message -like a crash or 'unexpected quit' warning- at the beginning of the burst of activity. Post those messages here - they are full of good information. 

(Etiquette: *Don't* post the whole file - that's considered rude in this forum. If the part you want to post is really long, put it in a pastebin and link to it)

Do the same in /var/log/messages and /var/log/dmesg

---

### Post by matt_symes on 2011-03-10
Hi

Is X crashing because of a screen saver (openGL maybe ?) and that is logging you out. 

Do you have a screen saver enabled ?

Open a terminal and type ( you might have to install the correct package: mesa-utils)

```
glxgears
```

Does it crash ?

DOH: Beaten to it.

Kind regards

---

### Post by jcoglan on 2011-03-10
> **Cheesehead said:**
> Does this *only* happen when the system is left idle? For how long? Has this ever happened while the system was not idle? If so, what were you doing?

It only happens when idle. I don't know for how long, it only happens when I'm away from the machine. If I remember to lock the screen with CTRL+ALT+L, it does not log me out.

> **Cheesehead said:**
> Does this happen only when certain software is running? Have you installed any unsupported software (like PPAs) around the time this issue began?

I don't remember when it started, it's been happening at least since I first posted this thread. I usually have these programs running: Chrome, Skype, Terminal (usually doing stuff with Ruby and ssh), Gedit (also editing over ssh), Firefox. I'm running Ubuntu 10.04.

> **Cheesehead said:**
> Open your power manager - how long is the delay until sleep/suspend?

Computer is set to never sleep, display is set to sleep after 30 minutes.

> **Cheesehead said:**
> Open the file /var/log/syslog and look for a time near one of the restarts (there should be a lot of activity around that time). Look for an error or warning message -like a crash or 'unexpected quit' warning- at the beginning of the burst of activity. Post those messages here - they are full of good information.

There's nothing odd there, just a cron job I have running every minute. (That's a recent addition, probably not to blame.)

> **Cheesehead said:**
> Do the same in /var/log/messages and /var/log/dmesg

Activity since I left the office last night:

Mar  9 20:39:39 chicago bonobo-activation-server (james-11312): could not associate with desktop session: Failed to connect to socket /tmp/dbus-El4mMUUroN: Connection refused
Mar 10 07:49:23 chicago rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="707" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 10 10:49:52 chicago pulseaudio[17496]: pid.c: Stale PID file, overwriting.
Mar 10 10:50:17 chicago kernel: [263001.458842] lo: Disabled Privacy Extensions
Mar 10 10:52:38 chicago pulseaudio[17496]: ratelimit.c: 3 events suppressed
Mar 10 10:59:39 chicago kernel: [263563.729321] lo: Disabled Privacy Extensions

---

### Post by matt_symes on 2011-03-10
Hi

Is it DPMS somehow crashing X ?

Open a terminal and type 

```
xset dpms force suspend
```

wake the monitor and type

```
xset dpms force standby
```

Do either of these crash X. And about the screen saver ?

Anything in /var/log/Xorg.0.log or /var/log/syslog to suggest what is happening ?

Kind regards

---

