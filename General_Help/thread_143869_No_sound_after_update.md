---
title: "No sound after update"
date: 2006-03-13
forum: General Help
---

### Post by loco on 2006-03-13
Hi, I have just updated my ubuntu breezy, and when I restarted (the update manager told me to do it) I have no sound at all, when I click on "volume control" it says:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


Dunno what happened cause the sound whas working perfectly before the update

I have a Realtek ALC850 integrated sound card AC97


Thanks :)

---

### Post by Xian on 2006-03-13
Register your gstreamer plugs and see if helps:

$ sudo gst-register-0.8

---

