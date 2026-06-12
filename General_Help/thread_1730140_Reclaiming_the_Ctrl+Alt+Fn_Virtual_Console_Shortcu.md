---
title: "Reclaiming the Ctrl+Alt+Fn Virtual Console Shortcut Keys"
date: 2011-04-15
forum: General Help
---

### Post by vista_convert on 2011-04-15
I have an IBM AT keyboard with the buckling spring key switches which I adore and from which I refuse to be parted. These keyboards do not have a Windows key or any of the nifty-multimedia keys. This was never a problem until Ubuntu introduced me to desktop shortcut keys that really work. (Curse you, Ubuntu!) 

You can guess what happened. One day, I decided to assign Ctrl+Alt+F8 to a custom shortcut (it couldn't have been F1-6) and that was when I discovered virtual consoles. 

(For those who may not know, virtual consoles is a UNIX tradition that apparently goes back to the Second Age of Middle Earth. There are twelve of them. Ctrl+Alt+F1-F6 activate text consoles. Your desktop normally lives at Ctrl+Alt+F7. F8-F12 are reserved for extra graphical desktops and by default plunge the unsuspecting novice into the Mines of Moria&#8212;a blank screen with a blinking cursor)

These keys cannot be reassigned with the Keyboard Shortcuts applet in Gnome, because they are grabbed before your desktop ever sees them&#8212;I suspect by the kernel, which is why I've classified this for all variants. I doubt it makes a difference. 

I don't need twelve virtual terminals. I do need shortcut keys. Is it possible to liberate some of these keys for the desktop? If so, how? Also, I would like to know where these keystrokes are grabbed. Is it the kernel? I'm writing a blog, you see, and I don't want to misinform my millions of readers. :)

One virtual text console is certainly handy for restarting your desktop (service gdm restart. Yes!) and probably for other things, but six seems like overkill. 

I would greatly appreciate any help at all. Thanks in advance.

P.S. I know how to shut off the getty services (by moving the /etc/init/tty?.conf files elsewhere), but that doesn't liberate the function keys. It just creates more entrances to the Mines of Moria.

---

