---
title: "Rhythmbox doesn't use NotifyOSD"
date: 2009-11-29
forum: General Help
---

### Post by GepettoBR on 2009-11-29
I suppose it should, since it's the default audio player in Ubuntu. Where's the desktop integration?

Most everything else seems to interact correctly with NotifyOSD. NetworkManager, Transmission, Empathy, Pidgin, Twitux and Exaile are just the ones I remember off the top of my head. Note: Exaile interacts with NotifyOSD in precisely the way I'd expect Rhythmbox to do.

I don't have a clue about how to configure any aspect of NotifyOSD, and found no packages to that effect in Synaptic. There also aren't any options in Rhythmbox. So, how do I get NotifyOSD to tell me when Rhythmbox changes tracks, pauses or starts playback, &c?

Using Ubuntu 9.10 Karmic Koala x64 with all updates installed.

Thanks in advance for any help,
Paulo Bittencourt

---

### Post by GepettoBR on 2009-12-06
One-week bump. Anyone?

---

### Post by mc4man on 2009-12-06
I use amarok and vlc where the notifications work fine, but maybe look in rhythmbox's edit -> plugins and see what's set

Edit; maybe just r. click on the little panel icon and ck. box

---

### Post by SciatoreItaliano on 2009-12-06
If I remember correctly, Rhythmbox only uses NotifyOSD if you click it's icon on the top panel to minimize it to the notification area. Try that.

---

### Post by GepettoBR on 2009-12-06
Thank you both very much! It turns out the default behavior really is to only use NotifyOSD when minimized to tray, but the tray icon plugin options allow me to change that. Now everything works.

---

