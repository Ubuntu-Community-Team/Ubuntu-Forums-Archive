---
title: "Help: notify-osd gets flood of notifications from indictor-sound"
date: 2011-07-13
forum: General Help
---

### Post by Vadrian on 2011-07-13
Recently (sometime between July 1 and yesterday), notify-osd has been going berserk, popping up the sound indicator, which flashes rapidly, causing the mute icon to appear, dropping the volume all the way down.  While this is occurring, the system is unusuable:  I can sometimes use the mouse, but Terminal windows are unresponsive.  

I can use ctrl-alt-f1 to open a TTY, kill notify-osd, and this clears things up temporarily.  

I ran notify-osd in debug mode, and it looks like it's being hit with a lot of indicator-sound events:[INDENT][FONT=Courier New]** (notify-osd:4350): DEBUG: Using icon parameter

loading icon 'notification-notification-audio-volume-medium' caused error: 'Icon 'notification-notification-audio-volume-medium' not present in theme'** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-medium (synchronous)]


** (notify-osd:4350): DEBUG: selecting monitor 0 at (0,0) - 1280x1024
** (notify-osd:4350): DEBUG: no panel detetected; using workarea fallback
** (notify-osd:4350): DEBUG: top corner at: 945, 22
** (notify-osd:4350): DEBUG: selecting monitor 0 at (0,0) - 1280x1024
** (notify-osd:4350): DEBUG: no panel detetected; using workarea fallback
** (notify-osd:4350): DEBUG: top corner at: 945, 22
** (notify-osd:4350): DEBUG: Using icon parameter

loading icon 'notification-notification-audio-volume-low' caused error: 'Icon 'notification-notification-audio-volume-low' not present in theme'** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-low (synchronous)]


** (notify-osd:4350): DEBUG: Using icon parameter

** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-low (synchronous)]


** (notify-osd:4350): DEBUG: Using icon parameter

** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-low (synchronous)]


** (notify-osd:4350): DEBUG: Using icon parameter

** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-low (synchronous)]


** (notify-osd:4350): DEBUG: Using icon parameter

** (notify-osd:4350): DEBUG: [2011-07-12T20:28:30-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-low (synchronous)]
[/FONT][/INDENT]... and so on.  The icon notification changes.  I see ...-muted, ...-medium as well.

This happens intermittently -- perhaps when a notification such as mail arrival is supposed to happen.

The sound card works: when I kill notify-osd and unmute, I can watch youtube videos just fine, with sound.

I had not changed the system before this started happening: no config changes, no updates, no upgrades.  The only thing is I removed a network drive that was USB-connected to our router -- shouldn't have had an effect.

I did update AFTERwards, and rebooted, but this didn't clear things up.

Can anyone help?

[INDENT][FONT=Courier New]uname -a = Linux myhoste 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
[/FONT][/INDENT]

---

### Post by Vadrian on 2011-07-13
My problem sounds a lot like this one: 
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/271706)

I tried remapping the volume shortcuts (which I don't use anyway).  So far, so good -- the problem had been happening multiple times a minute, and now it has been a couple of minutes since the problem has reared its head.  

Hopeful.

---

### Post by Vadrian on 2011-07-14
I think this is "solved," although technically there's still a mystery.

Remapping my volume keys eliminated the problem of notify-osd flashing rapidly and rendering my system unusable (until I could kill notify-osd by using ctrl-alt-f1 to get to a TTY).  In short, my system *seems* normal once again.

The remaining mystery is that this started happening in the first place.  I had made no software updates, installs, or upgrades immediately prior to the happening.  My best wild guess at this point is that I experienced some hardware failure which caused the mapped sound keys to start being registered as pressed, but I have no idea how to pursue that or even write it up.  If anyone reading this has thoughts or ideas for that, please email me.

---

