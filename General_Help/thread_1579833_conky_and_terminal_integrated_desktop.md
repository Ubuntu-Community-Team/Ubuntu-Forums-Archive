---
title: "conky and terminal integrated desktop"
date: 2010-09-22
forum: General Help
---

### Post by petrasflorin on 2010-09-22
this is how my desktop looks like (screenshot)

what is running there are conky - transparent background
and terminal - also transparent background AND undecorated.

my question is:
how do I integrate these into the desktop (I mean how do I make them both auto-start on startup and more importantly how do I make the terminal auto-undecorated from the beginning?)

I found some script for conky - trying that out right now, gonna let you know how it turns out.
in the meanwhile, any ideas ?

much appreciated.

---

### Post by Brandon Williams on 2010-09-22
The method for this will vary depending upon which desktop environment you are using. Your question is tagging with 'xfce', but the image appears to be an lxde desktop (at least the menu button looks like one from lxde).

With xfce, simply open the 'Session and Startup' dialog in the settings menu, select the 'Application Autostart' tab, and add items for both conky and the terminal. I think that lxde supports the freedesktop application autostart standard, but you might need to create the necessary autostart file by hand.

As far as running the terminal undecorated, this will also depend upon both the window manager and the terminal app you're using. When you start the terminal from the command line, is it automatically undecorated? Or do you have to do something to make it undecorated after the app starts?

---

### Post by Quackers on 2010-09-22
To start Conky on boot you can create a hidden file called eg .conky_start.sh and put it in your home folder. The contents of the file could be something like
#!/bin/bash
sleep 30 && conky;
where 30 is the delay wanted after startup for conky to display (sometimes needed).
Then go to System > Startup Applications and click on ADD
then in the box which opens in the top filed put conky or whatever you want to call it then for the command box just browse to the conky_start.sh file and highlight it then click on open. Then click on save and it should start on reboot.

---

### Post by petrasflorin on 2010-09-29
> **Quackers said:**
> To start Conky on boot you can create a hidden file called eg .conky_start.sh and put it in your home folder. The contents of the file could be something like
#!/bin/bash
sleep 30 && conky;
where 30 is the delay wanted after startup for conky to display (sometimes needed).
Then go to System > Startup Applications and click on ADD
then in the box which opens in the top filed put conky or whatever you want to call it then for the command box just browse to the conky_start.sh file and highlight it then click on open. Then click on save and it should start on reboot.

I tried doing that, there is no "ADD" button, just a list with appps I can check or uncheck for start-up.

---

### Post by petrasflorin on 2010-09-29
> **Brandon Williams said:**
> The method for this will vary depending upon which desktop environment you are using. Your question is tagging with 'xfce', but the image appears to be an lxde desktop (at least the menu button looks like one from lxde).

With xfce, simply open the 'Session and Startup' dialog in the settings menu, select the 'Application Autostart' tab, and add items for both conky and the terminal. I think that lxde supports the freedesktop application autostart standard, but you might need to create the necessary autostart file by hand.

As far as running the terminal undecorated, this will also depend upon both the window manager and the terminal app you're using. When you start the terminal from the command line, is it automatically undecorated? Or do you have to do something to make it undecorated after the app starts?

yeah, the screenshot is LXDE but I was wondering for LXDE and XFCE too.

anyway the terminal starts decorated and I have to undecorate it every time. I can't seem to be able to find a way to make it start un-decorated by default.

---

