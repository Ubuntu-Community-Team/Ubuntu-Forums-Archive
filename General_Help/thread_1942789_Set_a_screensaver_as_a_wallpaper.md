---
title: "Set a screensaver as a wallpaper?"
date: 2012-03-18
forum: General Help
---

### Post by zombifier25 on 2012-03-18
I use Ubuntu 12.04, using Plasma Desktop to render the background (since I love the plasma widgets, but not really KDE itself) and I have searched the web desperately for a way to make a screensaver act as a wallpaper on KDE, but no luck.
Can anyone help?

---

### Post by Zorael on 2012-03-20
There are some plasma wallpaper addons in the aptly named package **[plasma-wallpaper-addons](apt://plasma-wallpaper-addons)**, but there doesn't seem to be a screensaver one, no. I toyed around and the only way I found to work was with xscreensavers, so no asciiquarium.

The obvious route of starting a screensaver with --root (to get it to paint on the root window) didn't seem to work at all, but you can cook up a KWin window rule to make any xscreensaver start borderless, in fullscreen, on all desktops, always below all, initial placement on mainwindow, skipping taskbar/pager/switcher, not accepting focus and not being closable.

I'm attaching an example that seems to work -- at least for me. You can import it in System Settings -> Window Behaviour -> Window Rules. Then just start a screensaver; they're in **/usr/lib/xscreensaver/**.

Again, I could only get it to work with xscreensavers, so you'd need to install some xscreensaver* packages. They are in the main and universe repositories.

---

### Post by zombifier25 on 2012-03-22
Thank you for your help, but I kinda know how to do that. Sorry for not  clarifying, but my question is, can you do so WITHOUT overlapping the  plasma widgets? The plasma widgets are attached to the desktop itself,  and since no windows can stay below the desktop, the method doesn't work.

---

