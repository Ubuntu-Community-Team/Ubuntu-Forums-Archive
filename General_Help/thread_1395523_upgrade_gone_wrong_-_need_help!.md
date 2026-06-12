---
title: "upgrade gone wrong - need help!"
date: 2010-01-31
forum: General Help
---

### Post by dacyai on 2010-01-31
I'm at least a little more computer and ubuntu saavy than most people, but this one stumps me.  And I don't know how to phrase it in a googly way so that's out, but I'm wondering if someone knows how to fix this:  from the first boot after upgrading from hardy to jaunty, the menu and task bars are continuously appearing and disappearing.  The icons on my desktop shift to accommodate/un-accommodate them with each iteration.  It happens about 1.5 times per second.  The headings and icons on the menu take slightly longer to appear, like it's loading from scratch each time.  My keyboard shortcut to open a terminal won't work, but I used one of the ctrl+alt shells to look at top and it shows gnome-panel with continually increasing PIDs and never running longer than .5 seconds.  Is there an error log I can look at somewhere?  Any other ideas?  My desktop icons do work, however.. my system isn't really usable for, well, most of the things I use it for until I fix this.

---

### Post by Jotham on 2010-02-01
Can you give us some hardware info?
Also, did you upgrade from a previous installation? Edit: I mean, did you do a fresh install?

---

### Post by Jotham on 2010-02-01
This may be the same problem as [this]("http://ubuntuforums.org/showthread.php?t=1364243").

---

### Post by dacyai on 2010-02-01
Thank you for your quick replies.  I tried rm -r ~/.gconf/apps/panel as suggested in the other thread to no avail!  my hardware is intel core 2 duo, nvidia gtx video card, generic ddr2 800mhz memory, nforce type motherboard, nothing out of the ordinary..  jotham, it is an upgrade type installation and not a fresh install.  I'm confidant that 9.04 would work from a fresh install but I'm hesitant to format my hard disk.  Thanks for your replies, and thanks again to anyone with more advice.

---

### Post by Jotham on 2010-02-01
Did that command do anything at all?

Also, did you try the "killall gnome-panel" command?

Keep in mind you probably have to put "sudo" before some of these commands.

Sorry, I'm not at an Ubuntu computer right now so I can't test this stuff out myself.

I'm not a very technical user, but it sounds to me like the panels are repeatedly stopping and restarting. The increasing PID means (I think) that it's actually starting a new process every time.

Logs are in /var/log and you can view them in Gnome with the command "gnome-system-log &" according to [this]("http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/") page.

I realize this isn't very helpful, but my personal advice would be to just reinstall from disc. If you have settings or files you want to save, I can help you with that.

---

### Post by dacyai on 2010-02-01
thanks again, jotham, for replying.  I did try that command and it didn't work.  I was able to open a terminal from within X11 and try launching gnome-panel that way.  The message it crashes with is
```

gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libnotification-area-applet.so: undefined symbol: gtk-orientable-get-type

```
I think I'll back up my files and freshly install 9.10...

---

