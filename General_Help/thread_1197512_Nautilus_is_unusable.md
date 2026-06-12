---
title: "Nautilus is unusable"
date: 2009-06-26
forum: General Help
---

### Post by 311005901 on 2009-06-26
I can't open any locations in "Places>Home Folder or Desktop or Documents"
My desktop is also unresponsive.

Running nautilus in a terminal spits back:
```
(nautilus:3756): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:3756): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Running "gksu nautilus" works correctly.

I recently installed globalmenu, but it kept crashing so I removed it. I had to uncheck "/apps/gnome_settings_daemon/gtk-modules/globalmenu-gnome" in gconf-editor.
Could this have broken nautilus?

What can I do to get my filebrowser/desktop back?

---

### Post by gettinoriginal on 2009-06-26
I cannot find the post at the moment, but do remember someone saying they had to reinstall global menu, then uncheck "enable" before removing it.  There is also this thread, but it seems slightly different than yours.
[http://ubuntuforums.org/showthread.php?t=1151325&highlight=Places](http://ubuntuforums.org/showthread.php?t=1151325&highlight=Places)
Even though it was for different reasons, someone else also said to do the F2 > gksu nautilus > then in the window > view > reset view to defaults.

---

### Post by aysiu on 2009-06-26
It seems there are various fixes or workarounds for the bug. Nothing seems to be universally agreed upon, though:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/329146](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/329146)

---

### Post by 311005901 on 2009-07-16
Ok. For some reason, its fixed. :confused:
I don't know what I did, really...

---

