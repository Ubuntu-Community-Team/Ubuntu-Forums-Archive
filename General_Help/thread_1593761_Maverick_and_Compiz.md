---
title: "Maverick and Compiz"
date: 2010-10-11
forum: General Help
---

### Post by Clivest on 2010-10-11
Hi All

I have just upgraded to Maverick. I have successfully disabled Nautilus Desktop (I now have no items on my desktop). I then installed CCSM and the 'Extra Plugins'. I have configured a desktop cube and wobbly windows etc, but can't get CCSM to draw the wallpaper I put in the Wallpaper plugin.

I have attached a screenshot of CCSM.

Any idea why?

Thanks

Clivest

---

### Post by adpads on 2010-10-12
It's a bug in Maverick. The Wallpapers plugin is broken since upgrade.

Here's a bug report on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391")
Here's a bug report on freedesktop:
[http://bugs.freedesktop.org/show_bug.cgi?id=30260]("http://bugs.freedesktop.org/show_bug.cgi?id=30260")

Not ideal to upgrade on release day and find no desktop wallpaper, eh?

---

### Post by Clivest on 2010-10-13
Thanks for the links. I wondered if it might be some sort of bug. I'll wait for an update.

Just tried [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391/comments/6](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/629391/comments/6) (switch to a tty session and then back), and doing that draws the desktop.

---

### Post by adpads on 2010-10-13
Glad it helped
But why is this thread marked as solved? This workaround is not a fix - it temporarily causes the desktop wallpaper to be drawn correctly, but at restart the desktop still has a plain black background, cluttered with artifacts of any closed windows or items drawn on the screen.
I'm holding off on upgrading my other systems to maverick until this is fixed - is there a fix in the works?

---

### Post by Clivest on 2010-10-14
I guess I marked it as solved because I had a solution:
-Wait for a bug fix.
I'm a bit new here though, so maybe that wasn't appropriate.

I'm watching this [https://bugs.freedesktop.org/show_bug.cgi?id=30260](https://bugs.freedesktop.org/show_bug.cgi?id=30260) and haven't found a proper fix.

---

### Post by Jorin on 2010-10-24
[https://bugs.freedesktop.org/show_bug.cgi?id=30260](https://bugs.freedesktop.org/show_bug.cgi?id=30260)

This thread reports that the problem was fixed as of a few days ago. Someone provided an attachment (here: [https://bugs.freedesktop.org/attachment.cgi?id=39476](https://bugs.freedesktop.org/attachment.cgi?id=39476)). I have no idea what to do with that, though.

---

### Post by Clivest on 2010-11-05
Yeah I saw that as well. Just wait for it to come into the repos I guess, and update often.

---

