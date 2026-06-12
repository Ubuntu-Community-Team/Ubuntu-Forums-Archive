---
title: "100% Disk Space Utilized!?!?"
date: 2011-08-16
forum: General Help
---

### Post by Kissell on 2011-08-16
My system just crashed with a message that the /tmp space was full, and now after rebooting I can't login to gnome. 

I hit ALT-F1 to get to the command prompt and logged in and ran "df" and I noticed that my root partition is 100% full.  /tmp is part of the root partition.  I deleted everything in /tmp but it wasn't much stuff.  

I have a separate partition for /boot and /home and a separate swap partition.

Can someone please help me get logged in again!?  pretty please :)

It is a 12GB partition, that should be more than enough for the root partition...

EDIT: At the time of the crash, I was playing with "incron" a utility which monitors the file system.  It was supposed to act upon the creation of a new file in /media/Data (which is not part of the / partition).  The action was that it should copy using rsync any new files in that location to a backup on another disk.  I ended my statement with "\;" because other statements in incrontab were ended that way...  i wonder if it rsynced to my root partition because of that...???  I'll go investigate that possibility.

---

### Post by SoFl W on 2011-08-16
See this link
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Kissell on 2011-08-16
False alarm...  It had filled root...  with a folder called ";" so I didn't notice it when I did a directory listing...

---

