---
title: "unwanted ubuntu/gnome auto logout on idle??"
date: 2006-06-17
forum: General Help
---

### Post by Jiketsu on 2006-06-17
Hello,

I restarted my box for the first time in months, and since then I am having an issue. Gnome will just, log me out for no apparant reason and I have no idea why.

And I am not 100% if it only happens when Idle (but it really seems to be) but when I leave it sit for a little bit without doing anything, Gnome just signs me out automatically without asking and I am back at the login screen.

Its happened a few times now. I checked the screensaver options and other configurations within gnome but there's nothing there about logging out or or anything so I have no idea whats going. I checked the syslog and this is what it said about an earlier occurence:

Jun 17 03:31:56 localhost gconfd (chibi-13184): starting (version 2.12.0), pid 13184 user 'chibi'
Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at positi$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at posi$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readwrite:/home/chibi/.gconf" to a writable configuration source at position 2
Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at positio$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at posit$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at positio$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at posi$Jun 17 03:31:56 localhost gconfd (chibi-13184): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jun 17 03:32:02 localhost gconfd (chibi-13184): Resolved address "xml:readwrite:/home/chibi/.gconf" to a writable configuration source at position 0
Jun 17 03:41:58 localhost kernel: [4317072.385000] UDP: bad checksum. From 81.11.98.203:9243 to 70.102.277.216:16530 ulen 310
Jun 17 03:42:03 localhost gconfd (chibi-13184): Received signal 15, shutting down cleanly
Jun 17 03:42:03 localhost gconfd (chibi-13184): Exiting
Jun 17 03:42:03 localhost gdm[13099]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

So it receives a signal 15 and shuts down cleanly. Then it gets an error.. but that seems to be after the shutdown or? What is gconfd??

Thank yo so much for your help.. this has become very tedious :P

-Ji

---

### Post by protaginist on 2006-11-03
I had exactly the same problem and seem to have fixed it. I went into System - Preferences - ScreenSaver and unchecked Activate ScreenSaver When Computer is Idle.

My system ran unattended all night and was still logged in this morning. I have no idea why this worked, but it did in my case. The downside is that you have to use the power button to shut down the monitor. Let me know if this works for you. Maybe it is a bug in the software someplace. I update regularly and I think this started after one of those updates but don't know that for sure.

Bill

---

### Post by xtlosx on 2006-11-13
I have the same problem but when i unchecked Activate ScreenSaver When Computer is Idle., the second i unchecked it, my screen went blank and it just went back to the login screen... When i am in the screensaver options menu it goes REAL slow and lags until i  get out of it, another thing when i'm in Firefox and i page down or wheel mouse down it lags like crazy two.. i have a core 2 duo laptop, running amd64 6.10 edgy eft...... any ideas?

---

### Post by demijohn on 2006-11-21
See related thread (link below) ... people have been chasing down [COLOR="Red"]red herrings[/COLOR]
(like _syslogd_ restart and _cron/anacron_) but I really think the
X session zapping is due to screensaver bug ... as you seem to have
discovered.  So far, my X session has been up about 4 days and 
counting since I turned off gnome screensaver.  No answer and
haven't found an open bug.  Maybe someone who knows about such
things should open up a report ??  :-k 

[http://www.ubuntuforums.org/showthread.php?t=245216&page=5&highlight=daily+random+restart]("http://www.ubuntuforums.org/showthread.php?t=245216&page=5&highlight=daily+random+restart")

---

### Post by hairuo on 2007-05-18
I have the same question as u, when using firefox2.0. 
sometimes it will auto logout of gnome (ubuntu 7.04).
and my cpu is also 2 core amd64.

> **protaginist said:**
> I had exactly the same problem and seem to have fixed it. I went into System - Preferences - ScreenSaver and unchecked Activate ScreenSaver When Computer is Idle.

My system ran unattended all night and was still logged in this morning. I have no idea why this worked, but it did in my case. The downside is that you have to use the power button to shut down the monitor. Let me know if this works for you. Maybe it is a bug in the software someplace. I update regularly and I think this started after one of those updates but don't know that for sure.

Bill

---

### Post by armalite on 2007-07-10
Same for me with a Core 2 Duo and Nvidia 7600gs with nvidia proprietary drivers.

---

### Post by Person98 on 2008-01-07
i have the same problem although mine started when i enabled xinerama. I don't know if that helps but it was running fine until then. I know it wasn't an update because i haven't updated since 4 days before and everything until xinerama was running smoothly

---

### Post by H4ck3rx on 2008-01-16
Me too.
I'm using laptop Toshiba Satelite A135-S4407 + Ubuntu 7.10

---

### Post by trubshac on 2008-05-20
It's been a while since this thread was active, but I now have the same problem too:
I am running Hardy on a Dell C800 laptop.  It appears to auto-log me out whenever the screen save would kick in.  If I attempt to go to System-Preferences-Screen saver, it always logs me off immediately before I can change anyting.

Note that Hardy does not work 'out of the box' with the video card in this laptop - I had to manually set the monitor size to 1600x1200 before the display resolution could be set to match.  I would tell you what the video card is, but I can't remember what to type to find out!

Any suggestions on how to get around this would be gratefully received.

---

### Post by trubshac on 2008-05-21
Ok - I've found a work around so I'll post it here in case it helps anyone else with the problem:

Open a terminal window and type:
gnome-screensaver-command -i

this will inhibit the screen saver from starting.
Then run System->Preferences->Screensaver and disable the screen saver.

I now have no screen saver, but my PC doesn't log itself out.

---

