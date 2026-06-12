---
title: "Problem shutting down - restarts instead"
date: 2009-10-21
forum: General Help
---

### Post by lightstream on 2009-10-21
My ubuntu generally shuts down fine. I use the 'user switcher' applet on a panel to do the shutdown. This applet gives you choices of shutdown, restart, log out, hibernate etc, and its default behaviour is to pop up a second screen, which pretty much shows the same options even though you've already selected the one you want (shutdown in my case).

To be fair, there is a timer so that the action you selected will occur after a minute.

However I want to click once on a shutdown button, and have the computer shut down. So I have gone into the user switcher properties, and unchecked the box labelled 'show confirm dialogs for logout, restart and shutdown'.

It sounds like it should do exactly what I want, but when I choose 'shut down' with this option unchecked, the computer does not shut down, but instead restarts.

Pretty odd!

Can anyone confirm if this is a general bug with the switcher, or am I doing something wrong?

---

### Post by compiledkernel on 2009-10-21
Ive got a diag doc you should read through. I have to believe that something gets dumped to the logs at the time you perform the shutdown. 

[http://gwos.org/udsf/doku.php/hardware:diagnosis](http://gwos.org/udsf/doku.php/hardware:diagnosis)

Id say check syslog, then messages at the time you commit the action.

---

### Post by lightstream on 2009-10-21
Thanks for the guide, looks like a useful starting point for these types of things.

However ubuntuforums has done that thing it sometimes does, where a problem resolves itself as soon as you post about it!

What I did was change the power management setting so that when I press the power button the machine would shut down rather than ask me. After then, the user switcher then would shut down properly, without confirmation and without restarting. However if I set the power option back, it still works fine.

Very weird as it happened several times, even after I shut down by another method and turned back on.

I'm currently looking through the syslog to see if I can spot anything weird.

I'd like to get to the bottom of it even though I now have what I wanted, namely a computer that would shutdown with a single click :)

---

### Post by lightstream on 2009-10-21
Nothing in the logs looks out of place. At first I did think the following entries, which occur many times, meant the system was doing a restart not a shutdown, but now I think they mean it was doing a shutdown after all:

[B]Oct 21 21:14:05 osiris exiting on signal 15
Oct 21 21:15:09 osiris syslogd 1.5.0#5ubuntu3: restart.[/B]

---

