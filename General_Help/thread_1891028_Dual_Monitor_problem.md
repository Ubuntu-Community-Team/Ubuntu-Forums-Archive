---
title: "Dual Monitor problem"
date: 2011-12-04
forum: General Help
---

### Post by Heathicus on 2011-12-04
I am running Ubuntu 10.04.  My video card is an NIVIDIA GeForce 9800 GT. 

I use this PC as a file server and for XBMC.  One monitor is on a desk in my office.  The HDMI output goes to the living room TV on the other side of the wall.  The monitor shows the Ubuntu desktop while the TV is just used for XBMC.  We use the XBMC remote app on our phones to control it.

This PC is not used for much else.  Occasionally I will rip a DVD, or browse the web.

I followed instructions from these two pages to configure XBMC to open on the second monitor (TV), full screen, without capturing the mouse.  

[http://blog.burlock.org/xbmc/59-multiple-monitors-with-xbmc](http://blog.burlock.org/xbmc/59-multiple-monitors-with-xbmc)
[http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse](http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse)

I added the "xbmc-fs" script to my startup items so XBMC will automatically load when I reboot the computer.

Everything has been working great for over a year until today and I don't know what happened.  I did not install any updates.  I did not make any changes to the system.

Currently, I can see my desktop on the TV, and I see my cursor if I move it to that monitor, but nothing else.  I can't get any programs to load on that monitor.

If I open a terminal and type the commands from that script, sometimes XBMC opens on the desk monitor.  Sometimes it never opens.  Same thing if I replace the "XBMC" command with the command for another program.  Sometimes it opens in the desktop monitor, sometimes it never opens.

I've played around with the NVIDIA X Server Settings.  I've disabled the other monitor, changed to TwinView, enabled and disabled Xinerama (all that seemed to do was put the login prompt on the TV).  I've rewritten the X Configuration file, restarted X, rebooted.  All about 2 dozen times.  I've been working on this all day and it is driving me crazy!!

I'm at my wits end trying to figure out what the problem might be.  Help!

---

### Post by papibe on 2011-12-04
Hi Heathicus.

Could you post the content of these two files:
```
/var/log/Xorg.0.log

/etc/X11/xorg.conf
```
Paste their content separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post the links to them.

Kind Regards.

---

### Post by Heathicus on 2011-12-04
[http://paste.ubuntu.com/759902/](http://paste.ubuntu.com/759902/)

[http://paste.ubuntu.com/759904/](http://paste.ubuntu.com/759904/)

THANKS!

---

### Post by papibe on 2011-12-04
I have almost the same configuration: an Nvidia 9500GT connected using separate X screens to a Dell monitor and a Sony HDTV.

I compared your files with mines, and I can't seem to find anything wrong with them.

The only couple of thing I think are different is that I don't autostart XBMC, and I don't use any script, in other words, I don't use the desktop side and the XBMC side at the same time.

Does it work without those things?

Regards.

---

### Post by Heathicus on 2011-12-04
I have not tried taking the script out of my startup items.  But I have tried just running the script manually.  It seems to do absolutely nothing.  Even if I choose to run it in a terminal window, the window just disappears after a second or so.

I had been opening the NVIDIA X Server Settings by going to System -> Administration.  Reviewing the instructions I linked to in my first message, it says to start it from the command line ("gksudo nvidia-settings").  When I do that, I get this error:

ERROR: Cannot open display 'Punk-Ubuntu:0.1'.

Followed by a bunch of additional errors, such as:

```
ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).
```

I get those errors for lines 21 through 88 of nvidia-settings-rc.  The contents of that file can be seen here:  [http://paste.ubuntu.com/759965/](http://paste.ubuntu.com/759965/)

---

### Post by papibe on 2011-12-04
I remember something else: initially I got weird results when the TV was my primary monitor (the one that shows the BIOS' posts and goes to text mode when press Alt+Ctrl+F1).

Since every time I turn my computer on, the Dell Monitor is on (not always the TV in on), I literally switched DVI outputs, so that the monitor was my primary monitor.

After that everything has been working OK for me.

Regards.

---

### Post by Heathicus on 2011-12-04
The computer monitor is the primary monitor (where the BIOS messages are displayed).

I edited the "xbmc-fs" and commented out the line "DISPLAY=:0.1" and rebooted.  XBMC loaded, full screen but in window mode so the mouse wasn't captured as defined by the script, on the computer monitor.  The computer wallpaper was still visible on the TV.  So XBMC is working.  The script works.  It runs on startup.  X just can't open any windows on the second monitor.

I just remembered I had some difficulty when I was first setting this up and it ended up being something in Compiz.  I haven't messed with the Compiz settings in forever and I can't recall what the problem was back then or what the resolution was.  I'm not even 100% sure my memory is accurate on that.

---

### Post by Heathicus on 2011-12-05
Problem resolved!!

Line 30 of my Xorg.0.log file says:

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
```

THAT was the problem.  I reinstalled that font by running this command in a terminal:
[B]
sudo apt-get install xfonts-cyrillic[/B] Rebooted, and TV display with XBMC was working perfectly again!

Thanks, papibe!  Without your assistance, I would not have known to look at that log file.

---

### Post by papibe on 2011-12-05
I would've never thought of that. I have that warning too, but I didn't even know that may cause problems.

:D Glad is working for you.

Regards.

---

