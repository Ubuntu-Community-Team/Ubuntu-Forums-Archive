---
title: "ubuntu suddenly will only boot to shell"
date: 2010-04-14
forum: General Help
---

### Post by bloodofangels302 on 2010-04-14
This morning my laptop was booting fine into ubuntu 9.10. I shut it down normally and then later when I turned it on again it will show the ubuntu logo but then take me to a shell prompt for my username and password.  
I can log in, and have tried manually starting gdm but to no avail.  the commands I have tried are:
startx,
sudo /etc/init.d/gdm restart,
and also tried sudo dpkg-reconfigure xserver-xorg. 

None of these have worked.  The closest I have gotten is when I run startx I can see my desktop along with a few icons for a few moments before it goes back to the shell and says something along the lines of waiting for xserver to shut down Dropping master.  I have tried booting to an older kernel and into recovery mode but I get the same problem.  I was not updating or anything when I shut it down last so I really have no idea how this problem happened.  please help me out, thanks!

---

### Post by john newbuntu on 2010-04-14
Login to a terminal first and check the log files located in /var/log directory to see if you can spot any errors towards the end:

```
cat /var/log/syslog
cat /var/log/Xorg.0.log

```

---

### Post by bloodofangels302 on 2010-04-14
when I run cat /var/log/syslog I get a extremely large report with what looks like alot of errors.  the last few lines look like:

Apr 14 08:24:43 dell-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Apr 14 08:39:36 dell-desktop kernel: [ 908.191320] usb 2-3: USB disconnect, address 2

there are many lines which look like repeat the same kind of thing.

When I run cat /var/log/Xorg.0.log I get alot of messages like
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)

and

(II) intel(0): Modeline "1280x800"x60.0 74.95 1280 1296 1344 1498 800 801 804 834 +hsync -vsync (50.0 kHz)

over and over.  It then ends with the line

(II) intel(0): EDID for ouput DVI1


thanks for the help!

---

### Post by john newbuntu on 2010-04-15
what is the output from:
xrandr -q

Play around with your resolution settings as shown in this article and see if that helps.
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by aeiah on 2010-04-15
for future reference, when looking at log files on the command line its often easier to use less, as it'll allow you to scroll a page at a time with space and a line at a time with the arrow keys.
eg:

```

less /var/log/messages

```

---

### Post by muteXe on 2010-04-15
when you get to your prompt have you tried: CTRL + ALT + F7?

---

### Post by bloodofangels302 on 2010-04-17
Thanks for the help everyone but I just got impatient ended up reinstalling.

---

### Post by Josh K on 2010-04-17
Any way to configure it to boot into shell rather then start up the desktop environment? With the ability to then enter the desktop environment if I desire. Kinda like starting up into DOS and then typing "win" to then move to windows.

I'd prefer a fast startup rather then a desktop environment. I spend the majority of my time working in Terminal anyways, I figure why not just go straight there with the option to boot the gui if I need to.

---

