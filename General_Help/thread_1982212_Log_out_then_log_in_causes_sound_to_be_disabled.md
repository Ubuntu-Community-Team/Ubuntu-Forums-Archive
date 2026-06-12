---
title: "Log out then log in causes sound to be disabled"
date: 2012-05-18
forum: General Help
---

### Post by Paddy Landau on 2012-05-18
When I log out and log in again, the sound is disabled. It is enabled only after I restart the machine.

Normal working shows the applet as follows, before logging out and after logging in again:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218193&stc=1&d=1337329852[/IMG] [IMG]http://ubuntuforums.org/attachment.php?attachmentid=218195&stc=1&d=1337329852[/IMG]

I have also attached the sound settings, before and after.
Before: [attach]218194[/attach]
After: [attach]218196[/attach]

Any idea how to fix this?

---

### Post by steeldriver on 2012-05-18
this is a COMPLETE shot in the dark but if it's using pulseaudio, I wonder if your config dir (~/.pulse) has got corrupted or unwritable? it shouldn't hurt to just delete it and see if that helps

---

### Post by Paddy Landau on 2012-05-19
Thank you for your reply.

I have tried as you suggested, but unfortunately there is no change.

I think I shall have to raise a bug report.

---

### Post by Paddy Landau on 2012-05-23
I have raised a bug. If it affects you, please [visit the bug and vote]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1003310") for it (the green writing at the top-left of the page).

---

