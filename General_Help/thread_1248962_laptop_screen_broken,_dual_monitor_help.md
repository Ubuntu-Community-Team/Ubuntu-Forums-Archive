---
title: "laptop screen broken, dual monitor help"
date: 2009-08-24
forum: General Help
---

### Post by Xender1 on 2009-08-24
So my laptop screen is broken, all the pixels are messed up and can really only seen the top left portion the rest is all destroyed. Currently I am running ubuntu 9.04 and would like to be able to set up another monitor so I can still use my laptop. When I turn it on and it is doing bios stuff it gets displayed on my new monitor, but once the login screen pops the new monitor goes black and all the display is on my broken screen.

Anyone know how I can help fix that?

---

### Post by wanchai on 2009-08-25
Well, this is a little tricky, but you still have a bunch of options.

Dumb question upfront: Have you tried your Alt-Fn whatever combination that should toggle the modes on the external VGA connector?

Are you able to log in to a gnome session and launch a terminal without seeing anything? In my case it's easy because I have a keyboard short cut. If not, you need to know where to click to get the correct menu and then go up or down x steps, go right one, up/down again, etc. If you have two machines with the same setup you can do both in parallel. Anyhow, once you have terminal, type "gnome-display-properties" (maybe you can also open this directly using the same parallel approach). In gnome-display-properties press Alt-M, that should set mirror screen, then click Alt-A for apply. Maybe you're lucky then.

There are also some xrandr commands to switch the modes. In my notes files I found "xrandr --output VGA-0 --same-as LVDS --mode 1024x768", but I cannot verify this at the moment.

Another thing to try is to connect from another machine using "ssh -Y". Then you can start gnome apps and they will be displayed on the machine that's running the ssh. This requires that your laptop has an openssh-server installed. If it doesn't and you managed to get a terminal open, you can "sudo apt-get install openssh-server". You may also be able to use Alt-F1 to switch to a console and install openssh-server from there.

You can also try out the remote desktop viewer that comes with Ubuntu. Enabling this on the machine being viewed becomes little tricky again. You can start the remote desktop preferences form the command line with "vino-preferences". Hitting the space bar will toggle the first option that allows other users. Then try to connect from another machine. After a few seconds the viewed machine pops up a question whether you want to allow the connection. Press Alt-A.

And here is a link that tries to change the remote desktop preferences just from the command line. However, this link is a few years old and you may want to verify the settings on a working installation first.
[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

---

