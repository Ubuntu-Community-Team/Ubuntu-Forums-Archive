---
title: "Large downloads cutting out on browsers and wget"
date: 2009-08-23
forum: General Help
---

### Post by Marogian on 2009-08-23
Hi,

I've been having a bit of a weird problem I can't find any help with by searching or tinkering:
Downloading large files, >1GB, using Firefox, Epiphany and I just tried using Gwget, the frontend to wgetm seems to inexplicably cutout early. For example I tried to download a 2.2GB file on Firefox. It cut out at 200MB (I thought it had completed), it did this twice before I realised something was up. I tried it on Epiphany, same thing happened. I tried it on a completely different file on a different webserver, same problem, although not at 200MB, this got as far as ~500MB.

I tried it on Gwget and got 600MB of the file before it just stopped- it doesn't report it as finished, it just stops and nothing I can do seems to make it resume. The status is at "retrieving" but there's definitely no movement.

I'm using Ubuntu 9.04 32 bit edition...I'm on a wireless network but it hasn't cut out at all during any of the downloads, and nor has anything strange happened that I've noticed.

Does anyone have any ideas?

Suggestions would be most appreciated!

Cheers

btw sorry, I posted this on the Desktop Environments subforum by mistake :redface:

---

### Post by DFlame on 2009-08-23
Just a quick stab at this one - Have you run lspci (or lsusb if your wireless uses USB) and tried looking up the model of your card for any specific issues? 

If you can, repeat these tests with a wired connection and observe the results. Might help diagnose

---

### Post by Marogian on 2009-08-23
Thanks for the help!

There's no issues with the wireless card that I can see, but I'll go look for a wireless bridge tomorrow to see if that makes a difference.

---

### Post by Marogian on 2009-08-24
I just stuck it on a wired network-- no joy.

Does anyone else have any ideas?

I left the 2GB download on Gwget overnight and it appears to have downloaded a few hundred MB more overnight, its now on 1GB out of 2, but has completely stopped again. The Internet is most definitely working... large torrents, other smaller downloads etc all work perfectly...

:confused:

---

### Post by P4man on 2009-08-24
bittorrent would recover almost instantly if your connection died briefly, you would never notice. HTTP downloads would not.

It probably is your internet connection, but if you are behind a router, you wouldn't be able to tell, as the connection between the PC and the router would keep working, and the outages might be brief. I had that when I had my ADSL line upped to 4GB, which was too much for the line, as I was too far from the phone central. The line would desynch frequently, and it was hard to tell at the computer since the outages where only a few seconds. But HTTP downloads would stop.

FWIW, in my case, i usually got a new IP address with each disconnect. Perhaps you can check if your IP changes if you're on a dynamic IP.
to easily check your wan ip:

[http://whatismyip.com](http://whatismyip.com)

refresh that page when the download halted. if it changed, look no further.

---

### Post by Marogian on 2009-08-24
Thanks, it could indeed be that. But I know my IP address isn't changing between outages- if there are any- because I'm using apache2 with a static IP for some basic HTTP server stuff. I'd realise pretty quickly if my IP changed.

If it is random internet outages interrupting it, is there any download manager type program that would be capable of resuming the download if its interrupted?

I'm still not 100% this is the problem because I never seemed to have this problem before on Windows (admittedly ~8 months ago was the last time I used it)

There really is no other option but HTTP download for the thing I'm trying to download; its the installer for an MMORPG which isn't released in a box or via torrent...

---

### Post by P4man on 2009-08-24
well, another cause might be a problem with the router. You could try resetting it, or upgrading its firmware or try another one if thats a possibility.

As for a download manager. I guess there a few addons for firefox that do that, but it only works if the server supports resuming of aborted downloads, and if they do, I think by default firefox already resumes. I could be wrong tho.

BTW, I could also be wrong about the causes heh. If you think your computer is to blame, perhaps have a look in the log files, see if you notice anything out of the ordinary around the times the downloads halted.

---

### Post by Marogian on 2009-08-24
I'm at work atm so I'll have a look at logs & tinker with the router when I get home. I think as a quick fix I'll download the file from here and take it home on a USB... employers bandwidth exists to be abused.

Its not some kind of known problem then? That's kind of depressing ^_^

---

### Post by DFlame on 2009-08-25
I've encountered it before, with an unreliable router (BT Voyager 205 for the interested). With no difference between wired and wireless, it is likely a problem with your ISP or your router as P4man has deduced.

To be sure though, open the system log viewer (System, Administration, Log File Viewer. Or gnome-system-log from Terminal) then try a download. Any changes to the log files while you have the viewer open will be in **bold font**. Inspect them for anything that looks interesting as the download 'progresses'.

---

