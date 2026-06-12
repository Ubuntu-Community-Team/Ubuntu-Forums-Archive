---
title: "Ubuntu fails after 2 restarts"
date: 2009-09-13
forum: General Help
---

### Post by Valok on 2009-09-13
So I re-installed ubuntu 9.04 the other day after a short break to use openSUSE.  Everything was going just fine.  Installed the system, did all the updates I needed, restarted the computer and it was up and running great.

But once I restart the computer again, Ubuntu never loads back up.  Sometimes I will get a command line prompt to login to, but I get no graphical sessions, just a command line.  And other times, it gets stuck just trying to load the system up in the first place.

So for now I'm back on openSUSE which I'm really not a big fan of, please help!

---

### Post by stderr on 2009-09-13
When it gets stuck trying to load the system, try Ctrl+Alt+F1, and see if you're getting some useful messages. Also, what graphics card do you have, and did you install any drivers?

---

### Post by Valok on 2009-09-13
Thanks for the quick reply.

I'm using an Nvidia 8800GT video card.  And yes, I always have installed the recommended proprietary driver as part of the setup.  Could that be causing the problem?

And if so, what are my other driver options?

---

### Post by stderr on 2009-09-14
You could try running this and answering any questions it asks you: 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This will attempt to reconfigure your nvidia driver; aftr running through that, you would run

```
startx
``` 

to try to launch into the GUI. If that doesn't work, I'd see if you can boot into ubuntu's GUI by changing the video driver in /etc/X11/xorg.conf. You'll need something like:

```
sudo vim /etc/X11/xorg.conf
```

Replace 'vim' with a command line text editor you're happy using - emacs, nano, pico, ed (;)) etc.

In the section marked Section "Device" change the Driver (from I would imagine "nvidia") to "nv" (the open source nvidia driver) and see if that works - it may not. You start an X session with

```
startx
```

If that doesn't work, change it to "vesa" - that should boot into ubuntu's GUI successfully, but you won't want to remain using vesa for long.

If you manage to boot into the GUI, please post the contents of /var/log/dmesg - this may help us figure out what's going on.

---

### Post by Valok on 2009-09-14
Thanks a bunch!  And I can confirm that installing the proprietary driver is in fact causing the problem.  I'll be sure to give all this a go soon and report back.

---

### Post by Valok on 2009-09-15
Alrighty, so I had a brief moment with my computer this morning, and this is what I got.

When running the command "startx", I got an error saying it couldn't be started.  After looking into the /xorg.o.log file, I found the following errors.

```
EE: no deviced detected
Fatal Error: no screens found
```

I hope this helps shed some light on an answer!

---

### Post by Valok on 2009-09-15
So some more info, even after reconfiguring xorg, I still get the same error from trying to run startx.

When I go into edit the xorg.conf file however, it doesn't say anything under the device section about a video driver, it just says...

```
Section "Device"
           Identifier                 "Configured Video Device"
EndSection
```

---

