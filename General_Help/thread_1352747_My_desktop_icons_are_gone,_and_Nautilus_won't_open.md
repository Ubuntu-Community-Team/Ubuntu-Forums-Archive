---
title: "My desktop icons are gone, and Nautilus won't open to browse files"
date: 2009-12-12
forum: General Help
---

### Post by Doughy on 2009-12-12
I had a bad Nautilus problem come up on my laptop today.  All of my desktop icons are gone, although the files are still there when I look from the command line.  When I try to go to "Places -> Desktop" or any other folder, it tries to open Nautilus, but then nothing happens.  I have tried rebooting, but it's just not working.  Any ideas?

Ubuntu 9.10 with integrated Intel graphics.

---

### Post by MaindotC on 2009-12-12
Are you dual booting and if so did you properly shut down Vista?

---

### Post by jacobs444 on 2009-12-12
try changing to 1024X768 resolution, if they come back then it is a general error with the driver I believe.

---

### Post by Doughy on 2009-12-12
> **strAlan said:**
> Are you dual booting and if so did you properly shut down Vista?

Not a dual boot.  Only OS installed is Ubuntu 9.10.  Also, I tried changing display dimensions, no luck.  I don't believe it to be a graphics problem since I can't even run Nautilus to browse files.

---

### Post by itsjustarumour on 2009-12-12
I think I've been having this problem on Jaunty 9.04, straight after some updates 2 or 3 days ago.  My system froze, and then the Screenlets on my desktop disappeared.  After a reboot, SuperKaramba and AWN disappeared. I tried opening my Home Folder, all my files opened with Gwenview instead of Nautilus. I uninstalled Gwenview, but then my files opened with Dolphin.  I tried rebooting again, and I was confronted with just my Desktop wallpaper and the cursor - nothing worked, I couldn't even invoke any programs with keyboard shortcuts.  

I hadn't changed any settings or file permissions or anything, this was just a random case of spontaneous config-file corruption.  I haven't managed to find a bug report anywhere that relates to this, and I can't file a bug report myself right now as I don't have all the necessary info to describe exactly what happened and why...  

The basic problem seems to be that Nautilus isn't starting on login...

I have tried - in turn - recreating the following config files in my Home directory, but this made no difference:

~/.config
~/.gconf
~/.gconfd
~/.nautilus

I did however discover that if I go to ~/.local/share/applications , if I temporarily remove all 4 Nautilus desktop config files (I just created a folder at this location called "NautilusBACKUP" and put them in there), if I log off and on again, my Desktop icons load up.  I can also then right mouse-click on the Desktop to fire up a terminal, and from that terminal launch gnome-panel, avant-window-navigator, screenlets etc.  My home directory also then opens with Nautilus, rather than Dolphin.

Sorry I can't provide any more concrete info at the moment, but I'm still trying to work out a fix for this.  I just thought I'd post up my "interim findings" as I've seen one of two other threads on the forum with peeople having issues that might relate to this...

---

### Post by Doughy on 2009-12-12
I found a fix for this problem.  According to this bug report, some gvfs stuff got corrupted: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/424043](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/424043)

I moved the ~/.local/share/gvfs-metadata to a backup directory and now the problem is fixed.

---

