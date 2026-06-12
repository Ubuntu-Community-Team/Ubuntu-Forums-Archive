---
title: "how do I restart my sound after hibernate?"
date: 2006-03-31
forum: General Help
---

### Post by jjf on 2006-03-31
When my laptop comes out of hiberate, the sound no longer works.  A bit of Internet research uncovers this as a bona fide bug in Breezy:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/4215](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/4215)

In order to get it working again, I've been restarting gnome (ctrl-alt-backspace).  But I'm sure there's some way to restart just the sound program without killing all of gnome.  Here's what the link above recommended:
```
/etc/init.d/alsa force-unload
/etc/init.d/hotplug restart
```

The first command works fine.  The second command doesn't work.  It returns this error:
```
sudo: /etc/init.d: command not found
```

What command can I use to restart the sound?  Thanks.

---

### Post by Ubuntuud on 2006-03-31
Maybe you should try "start" instead of "restart"... You could also try esd.

---

### Post by darkaudit on 2006-07-30
None of that worked here. I did > /etc/init.d/alsa-utils reset and all was well. Sound now works normally. :)

---

