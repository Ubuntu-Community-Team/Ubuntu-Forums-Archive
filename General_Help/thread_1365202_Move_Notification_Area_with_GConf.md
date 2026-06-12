---
title: "Move Notification Area with GConf"
date: 2009-12-26
forum: General Help
---

### Post by rfkrocktk on 2009-12-26
Is there a way to move the notification area where popups occur? I know there's gotta be some setting in GConf somewhere that I'm missing, could someone point me in the right direction? I'd like to be able to customize the x/y position. 

I tweaked my desktop a lot and now notifications look completely out of place (see screenshot).

---

### Post by Ben Wright on 2009-12-26
The daemon that manages those pop ups is called: notify-osd. I believe this wiki article covers what you are looking for: [https://wiki.ubuntu.com/NotifyOSD#position](https://wiki.ubuntu.com/NotifyOSD#position) . Thanks

---

### Post by rfkrocktk on 2009-12-26
I have disabled gnome-panel from being started by renaming it. So, I think that notify-osd is thinking that gnome-panel is still running and trying to reposition itself under the nonexistent panel. I don't see any way to move the notifications from the link you sent me. Do you have any other ideas that I might try? :)

---

