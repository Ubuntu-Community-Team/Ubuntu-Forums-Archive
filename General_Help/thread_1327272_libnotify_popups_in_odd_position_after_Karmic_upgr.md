---
title: "libnotify popups in odd position after Karmic upgrade"
date: 2009-11-15
forum: General Help
---

### Post by azzid on 2009-11-15
Since I upgraded to Karmic Koala my libnotify popups have shifted position, they now popup right below where they used to, as if to leave room for the old popups.

Is this something I can configure? How?

The only app (more or less) I have that uses this feature is pidgin, but the configuration UI for that functionality in pidgin is very limited (on/off).

---

### Post by username-is-mine on 2009-11-17
just wanted to bump this thread as it's super annoying that these things show up in stupid locations.  I'm running a clean install of 9.10.

screen shot - [http://imgur.com/qqIvK](http://imgur.com/qqIvK)

---

### Post by asmallerbrain on 2009-12-02
bump.  Same issues here.  I'll see what I can figure out.

Generally the popups are super-annoying and not configurable.  This is a bad combination!

I want them to go away.  So I move my mouse over them in hopes I can click them out of existence.  They slightly dim as if to say "I'm a ghost!  You can't touch me!  WHHHHOOOOOT!"

I really like some of the visual effects in Karmic.  This is not one.  I think notifications are useful but I really wish they could be configured to be single-line (e.g. no higher than the title bars on client windows).

---

### Post by endBc on 2009-12-02
[i386]("https://edge.launchpad.net/%7Egilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2%7Egilir1_i386.deb") | [amd64]("https://launchpad.net/%7Egilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2%7Egilir1_amd64.deb") - download, install, reboot. It'll revert notify-osd settings back to how they were on 9.04.

---

### Post by azzid on 2009-12-02
Just a little FYI: this [bug]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894") is a [feature]("https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble")...

---

