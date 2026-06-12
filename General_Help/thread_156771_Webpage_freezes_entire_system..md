---
title: "Webpage freezes entire system."
date: 2006-04-07
forum: General Help
---

### Post by BoboChimp on 2006-04-07
I've got a new Breezy install and when i go to [www.cnet.com](www.cnet.com) with either Firefox or Opera the entire box freezes within a few seconds after the page starts loading.

After install, i got Automatix.  Here is my Automatix.log file contenets:
Acrobat Reader
Archiving Tools
AUD-DVD codecs
Bittorrent Clients
Ctrl-Alt-Del
Firefox 1.0.7 Plugins
Frostwire
GFTP
Gnomebaker
MS TTF Fonts
Media Players
Multimedia codecs
Multimedia Editing
Open Office
SUN JAVA 1.5 JRE
Firefox 1.5.0.1
Gdesklets
Gnome Sound fix

I don't think this is an Automatix problem, i just want you guys to know what i installed.  

I did a stint a while back where i installed FC4 on this box but i just didn't have the time to invest in what i needed to learn then.  From that time though, I remember if there was a problem, you could review some logs to see what was happening when the crash occured.

Is that the best place to start trying to troubleshoot this problem?  I really don't know where to start but I'm willing to invest the time.

I have to warn you though, i may not be able to be as responsive as i want to be b/c the wife doesn't like me "on the computer" all the time.  I will answer any questions you have, jut might take some time.

---

### Post by trent dillman on 2006-04-07
You may want to search through Synaptic and see if there's anything swf-related. Possibly a Flash issue.

---

### Post by BoboChimp on 2006-04-09
well i think i downloaded and installed everything related to flash through synaptic.  i also reinstalled those that i had already installed.  I'm going to keep looking around for a way to figure this out.  if anyone has an idea of where to start or what steps to take from here, i'm all ears.

---

### Post by John Doe on 2006-04-10
I had this unusual issue myself a while ago and found out that it was caused by a filesystem error that ext3's journal somehow did not catch on its own that required a full "fsck" (filesystem check) of one or more of my partitions.  After a filesystem check using "e2fsck -f -p" of all my ext3 partitions (done from ubuntu's live CD), the problem completely disappeared.

---

### Post by BoboChimp on 2006-04-10
I'll keep that in mind if it happens again.  As it turns out, i got tired of trying to find an answer so i took the Windows approach and reinstalled the OS.  I figured since it was a pretty new install anyway and i hadn't spent a lot of time trying to configure everything, i didn't have anything to lose that i couldn't recreate anyway.

this time, i installed everything one at a time so try to troubleshoot what caused the problem originally.  I used Automatix to install the plugins for Firefox 1.07 but now, flash doesn't show up on webpages.  i guess that is better than having it freeze the system :)

during my research of the originial problem i managed to learn a lot so i don't consider it a waste of time by any means.  that's the whole reason i grabbed linux/ubuntu.  i was bored with windows and wanted a new challenge.

now i just have to figure out how to make flash animations work.  i'm sure there is a lot more documentation and threads on that than on the original problem.

---

### Post by BoboChimp on 2006-04-10
problem solved.  i found this thread on accident...
[http://ubuntuforums.org/showthread.php?t=89827](http://ubuntuforums.org/showthread.php?t=89827)

this site is so vast i didn't find that thread when i was searching for a solution to the original problem.

Big thanks to arnieboy!

---

### Post by SteelCore on 2006-04-16
[QUOTE=BoboChimp]
[http://ubuntuforums.org/showthread.php?t=89827](http://ubuntuforums.org/showthread.php?t=89827)
[/QUOTE]

I changed the settings according to the link and firefox still freezes :(

---

### Post by towsonu2003 on 2006-04-16
I don't get a crash in that site (using 1.5.0.2). may be an extension issue? or corrupted profile? For extensions/plug ins, try starting firefox from terminal with
```

firefox --safe-mode

```

if it crashes again, check out the output. may give you insight. copy paste here if you'd like. 

if corrupted profile (trial and error here to see if it's so), close firefox, move your profile away, and try again: 
```

cp -R ~/.mozilla/firefox ~/.mozilla/firefox.busted

```
You'll loose bookmarks, plugins and what not. Bookmarks will go to ~/.mozilla/firefox.busted/<randomnumbers>.default/bookmarks.html

if crashes again with a brand new profile, I'm clueless. close firefox and restore profile with 
```

cp -R ~/.mozilla/firefox.busted ~/.mozilla/firefox
```
and maybe file a bug to firefox bugzilla?

---

### Post by SteelCore on 2006-04-16
Thanx, I'll give it a try.

---

