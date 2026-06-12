---
title: "Display notifications over xscreensaver"
date: 2011-09-28
forum: General Help
---

### Post by gnick on 2011-09-28
Hi,

I'm currently playing around with notifications, and I'm trying to "keep" notifications displayed above the screensaver, so that I can see if I've got new mail or an IM from afar, without having to unlock my pc.

Basically the opposite problem to these: 
- [http://www.jwz.org/xscreensaver/faq.html#popup-windows](http://www.jwz.org/xscreensaver/faq.html#popup-windows)
- [http://www.google.com/search?q=notifications+over+screensaver+ubuntu](http://www.google.com/search?q=notifications+over+screensaver+ubuntu)

I'm using a command similar to the following, to display messages with an infinite timeout:
```
$ notify-send -t 0 -i info "You've got mail" "mailbox (123)"
```Currently notifications get displayed temporarily "above" the xscreensaver, but eventually xscreensaver will "raise" itself above the notification (e.g. after a minute or two).

Here are my options, as I see it currently:

1) Download the xscreensaver's source code, modify it to prevent it raising itself above the notifications, build and install it (painful... I've managed to build it from the source, but I don't know what I should be modifying.)

2) Write my own custom screensaver (not really path I want to take, when I already have a notification and screensaver framework).

Are there any other (easier) options I've missed? Can anyone help?

(There's an argument that nothing should be displayed over the top of screensavers... :()

Some context:
Ubuntu 11.04
Unity
notification-daemon/natty uptodate 0.5.0-2ubuntu1 (or notify-osd)
xscreensaver/natty uptodate 5.12-0ubuntu3 (I haven't tried gnome-screensaver)

---

