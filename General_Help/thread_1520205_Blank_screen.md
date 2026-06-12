---
title: "Blank screen"
date: 2010-06-29
forum: General Help
---

### Post by daudaudaudau on 2010-06-29
Hi.

Today when I turned on my computer the screen was just blank and said "No signal". So I tried moving the DVI-cable to the other port on my gfx card, and then I could see the computer booting up and I could see the Ubuntu logo while booting. But just before the desktop is supposed to appear, the screen goes blank again saying "No signal".

At this point I moved the mouse to the upper right corner of the screen (without being able to see it) and I was able to shut down the computer. While the computer is shutting down the Ubuntu logo appears on my screen again. So it seems that it is only the desktop that will not show up. What can I do about this?

---

### Post by gzarkadas on 2010-06-29
Let's analyse the event:

> **daudaudaudau said:**
> ...when I turned on my computer the screen was just blank and said "No signal". 

So, text mode (what the computer starts with) does not send signal to monitor when cable is in port #1.

> **daudaudaudau said:**
> So I tried moving the DVI-cable to the other port on my gfx card, and then I could see the computer booting up and I could see the Ubuntu logo while booting. But just before the desktop is supposed to appear, the screen goes blank again saying "No signal".

Putting cable to port #2 restores (?) text mode (yes, if you saw lines filling up the screen) and standard VESA mode which is used up to the login screen. But fails on high-fidelity graphics mode; the card does not send high-resolution signal to monitor when cable is in port #2.

> **daudaudaudau said:**
>  At this point I moved the mouse to the upper right corner of the screen (without being able to see it) and I was able to shut down the computer. 

Not seeing it, but having it working means the software is functional and no fatal errors in your card that would make Xserver fail were detected.

> **daudaudaudau said:**
> While the computer is shutting down the Ubuntu logo appears on my screen again. So it seems that it is only the desktop that will not show up. What can I do about this?

Expected, since the VESA mode also worked at the startup.

Conclusion:

I make the guess that there is a problem with your cable. So your first move would be to find another one and test it. The next point to look is your card, especially the pins at the output plugs; inspect them for dirt or damage. 

Ensure also that the card has not been constantly overheated in the past; this, if happened may have create some minor damage that manifests itself as this erratic behaviour. You may borrow a card from a friend to check it, if the cable is found right.

---

### Post by daudaudaudau on 2010-06-29
I just tried with a VGA cable and a DVI-to-VGA converter I have. The situation is the same except now the screen turns on when I use port 1 on the gfx card, where it said "No signal" before. The screen is still blank though. So I guess it's not the cable. 

Is it not possible to make Ubuntu use the other port for desktop output? I can get to the console by pressing Ctrl+Alt+F1, but I don't know what to do there.

---

### Post by gzarkadas on 2010-06-29
If there is a problem with the card, I doubt whether switching ports can be a viable solution. However since now you have a console, we maybe able to see what are the errors; login and then type:
```

cat .xsession-errors | less

```Try to locate lines that relate to your graphics card, to figure out whether an error is registered or not. 

After that type:
```

cd /var/log
cat Xorg.0.log | less

```Do the same thing with that file also.

Also, being in /var have a look to your syslog
```

sudo cat syslog | less
# **if syslog has only a few lines**, it has been rotated recently; 
# **then use the following: **
sudo cat syslog.1 | less

```and to your dmesg
```

sudo cat dmesg | less
# **if syslog has only a few lines**, it has been rotated recently; 
# **then use the following: **
sudo cat dmesg.0 | less
 
```The files above tend to be long. To cut scrolling through them, you can use instead of `| less' the following: `| tail -n 1000 | less'  (or 500 instead of 1000)  to make the list shorter. Don't short it too much else you risk not catching the error.

You can also type:
```

sudo lspci | less
sudo lshw | less
sudo lshw | grep UNCLAIMED

```to show information about your pci and hardware status. The last line is to catch devices with a driver problem.

---

### Post by daudaudaudau on 2010-06-29
I tried booting first with the screen attached to port 1 (blank screen) and then with port 2. So I guess the ".old"-files refer to the startup with port 1.

These are the things I thought might be relevant

In .xsession-errors:
(gnome-settings-daemon:1601): GLib-CRITICAL **: g_propagate_error: assertion 'src!=NULL' failed
UNable to find a synaptics device.
Checking for Xgl: not present


In .xsession-errors.old:
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0
gnome-volume-control-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0


In Xorg.0.log:
Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
    CRT-0
    ViewSonic VP930 (CRT-1)
CRT-0: 400 MHZ maximum pixel clock
ViewSonic VP930 (CRT-1): 400 MHz maximum pixel clock
Assigned display device: CRT-0


In Xorg.0.log.old:
Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
    ViewSonic VP930 (CRT-0)
ViewSonic VP930 (CRT-0): 400 MHz maximum pixel clock
Assigned Display Device: CRT-0

In syslog:
Jun 29 12:47:12 ahg kernal: [   0.098268] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
(several of these lines)



It looks like it is able to detect my screen just fine.... Can't we just assign it to a different display device? I.e. instead of using CRT-0 in Xorg.0.log, it should be using CRT-1.

---

### Post by gzarkadas on 2010-06-29
Those few lines in isolation cannot provide a clue. Please post the .xession-errors and Xorg.0.log as attachments. Also post your /etc/X11/xorg.conf.

A test to screen out the possibility that the graphics card is faulty, is to plug it into another computer and verify that it works fine. This is something that has to be done if a quick solution cannot be found, because we could spend days trying to debug something that is not trully debugable; if the harware is faulty, it *is* faulty, period. Nothing can be done.

---

### Post by daudaudaudau on 2010-06-30
It probably is faulty since the screen is blank even before the operating system starts doing anything. But I don't want to buy a new card if I can just use the other port. Isn't is possible to use the other port?

---

### Post by dino99 on 2010-06-30
remove "quiet splash" on the boot line (edit it from grub menu) to see comments when booting and know what happen in the background

---

### Post by gzarkadas on 2010-06-30
Yes, and post the logs; we may be able to find something from there that can help your cause :).

---

