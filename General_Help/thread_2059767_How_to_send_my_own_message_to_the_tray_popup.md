---
title: "How to send my own message to the tray popup?"
date: 2012-09-18
forum: General Help
---

### Post by pdepedo on 2012-09-18
Hi, I'm using i3 as my window manager, and I saw that Clementine has an option to send messages about the songs/volume as a little popup in the tray bar, and I was wondering if there's a way I can use that myself, because when I press the volume keys the volume changes but I don't get any notifications and I'd like at least a tray popup.

I suppose Clementine sends a message to another application that shows the popup? I just don't know how to find out which application or how to send a message myself.

Thank you

---

### Post by december0123 on 2012-09-18
Try this:
```
 notify-send <title> <message> 
```

---

### Post by pdepedo on 2012-09-18
Yes, I tried that before, but I get a notification that is controlled by the xfce4 notification program which is not what i want.

Here's a screenshot: You can see the message from xfce4-notifyd and then in the bottom right corner you can see the tray popup that Clementine shows when I change the song. Is that one popup that I want to be able to recreate.

---

