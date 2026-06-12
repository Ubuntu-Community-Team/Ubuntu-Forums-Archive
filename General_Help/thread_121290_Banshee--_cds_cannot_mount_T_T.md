---
title: "Banshee-- cds cannot mount T_T"
date: 2006-01-24
forum: General Help
---

### Post by mztriz on 2006-01-24
I'm not sure what I'm doing wrong. Banshee used to work just fine and today I upgraded to the newer version so I could use the audioscrobbler plugin. I installed it by adding deb [deb http://apt.filefind.net/ breezy main contrib non-free](deb http://apt.filefind.net/ breezy main contrib non-free) breezy main contrib non-free to my sources.list and then just upgrading. Everything appeared to work just fine, banshee opens and plays with no problems; except cds. I will put in a cd and it doesn't show up in banshee as it normally did and so I try to 'import folder' and I go to cd-rom and it says 'Could not mount CD-ROM/DVD-ROM Drive'.

Any Ideas?

Thanks,
Ava.

---

### Post by mztriz on 2006-01-25
Edit: Double post..

---

### Post by mztriz on 2006-01-28
Anyone have any ideas?

---

### Post by Simian on 2006-02-03
I have the same problem. But it started when I upgraded to dapper. Did you find out how to fix it?

---

### Post by mztriz on 2006-02-04
No I don't sorry; I never figured it out it's also doing the same thing on my other computer. I'm using breezy though.

---

### Post by GreySim on 2006-02-05
I also am having the problem on a freshly installed Breezy with practically nothing upgraded other than what was upgraded as part of the Banshee install.

I filed a bug report and am lurking in the #banshee channel on irc.gnome.org looking for an answer.  :)

---

### Post by GreySim on 2006-02-06
Forgot to actually link to the [bug](http://bugzilla.gnome.org/show_bug.cgi?id=329966).

It seems that the key problem can be found by running banshee from a terminal (in my case, anyway).

```

** (<unknown>:13651): WARNING **: Symbol file
/usr/lib/mono/gac/dbus-sharp/0.36.2.0__9eef2692033670f5/dbus-sharp.dll.mdb has
incorrect version (expected 39, got 38)
Warning: [2/6/2006 8:51:55 PM] (Cannot connect to NetworkManager) - An
available, working network connection will be assumed
Debug: [2/6/2006 8:51:56 PM] (Changed active playback engine) - GStreamer
Debug: [2/6/2006 8:51:56 PM] (Loaded primary playback engine) - GStreamer
Debug: [2/6/2006 8:51:56 PM] (Loaded Audio CD playback engine) - GStreamer
Debug: [2/6/2006 8:51:56 PM] (Audio CD Core Initialized) -
Warning: [2/6/2006 8:51:59 PM] (Could not connect to D-Bus) - D-Bus support
will be disabled for this instance: Object reference not set to an instance of
an object
Scanning library for tracks to update
Done scanning library
Processing track queue for pending queries
Done processing track queue

```

---

### Post by kaamos on 2006-02-07
Same output and problem here with mono 1.1.13.2 and banshee 0.10.4.

EDIT: actually, I have the same output, but now that I tried the cd played just fine.

---

### Post by mztriz on 2006-02-10
[QUOTE=kaamos]Same output and problem here with mono 1.1.13.2 and banshee 0.10.4.

EDIT: actually, I have the same output, but now that I tried the cd played just fine.[/QUOTE]

Really that's amazing, I guess I'll have to try to open it from terminal next time. I tried to reinstall banshee but synaptic went crazy and it doesn't let me.

---

