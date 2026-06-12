---
title: "Rhythmbox takes 20sec to start?"
date: 2012-03-27
forum: General Help
---

### Post by kurja on 2012-03-27
Rhythmbox music player is very, very slow to start, it takes like 20 seconds (which is almost as long as it takes to start the whole 'puter!). I have tried disabling "watch my library for new files", no noticeable effect. Rhythmbox version is 2.95. If I start it from terminal, I get this: ```
(rhythmbox:3094): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

(rhythmbox:3094): libdmapsharing-WARNING **: Unable to initialize mDNS: Daemon not running

(rhythmbox:3094): libdmapsharing-WARNING **: Unable to notify network of media sharing: The avahi MDNS service is not running

(rhythmbox:3094): GLib-GIO-CRITICAL **: GApplication subclass 'RBShell' failed to chain up on ::startup (from start of override function)

```Multicast DNS? Huhwhat?

---

### Post by kurja on 2012-03-27
found here [https://bbs.archlinux.org/viewtopic.php?id=108544](https://bbs.archlinux.org/viewtopic.php?id=108544)

> 1. Open Rhythmbox
2. Select from menu: Edit -> Plugins
3. Disable "DAAP Music Sharing" plugin

which seems to work around the issue well enough, at least it starts up quicker now.

---

### Post by Orion8 on 2012-05-29
Thanks for posting this.  It fixed a very annoying problem for me!

---

### Post by Andre-D on 2012-11-22
yes, thanks - annoying for mee too.

---

