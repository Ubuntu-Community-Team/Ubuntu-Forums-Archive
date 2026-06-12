---
title: "Load Rise Of Death (LROD)"
date: 2009-08-20
forum: General Help
---

### Post by daltore on 2009-08-20
I've found the Ubuntu counterpart to the Windows BSOD (Blue Screen Of Death).  At seemingly random times, the load monitor on my tool bar (the gnome-system-monitor applet, using all 6 monitors) will begin to rise, and at that point, I can't exit programs, start new programs, change desktops, or really do anything useful (mouse still moves around, and I can sometimes still type in windows for a while), and I have to manually reboot (hold power button down for 5 seconds).

The strangest part is, that none of the other monitors show a corresponding increase.  Memory, processor, SWAP, network, and hard drive all stay roughly constant, and around their normal levels, it's just the load.

Does anyone know why this might be, and more importantly, what I can do about it?


Thank you,
Aaron

---

### Post by P4man on 2009-08-21
im not even sure what "load" measures.. isn't it an average of cpu usage?
either way, you might want to try running system monitor from system > administration and ensure you show processes for "all", not just yourself.

Alternatively, run top from the command line. Im guessing something is leaking memory badly, but that applet isn't picking it up because whatever is causing it,is not running with your account (but probably as root) ?

---

### Post by macunixfan on 2009-08-21
Could it be that indexing service?

---

### Post by DGortze380 on 2009-08-21
First stop with the hard reboots, they're doing more harm than good.

Press:
ctrl+alt+F1 
to get to a virtual terminal. 

There are a number of things you can do from here. My first suggestions is the top command to see which processes are running.

```
sudo top
```

type 'q' to quit top. You can use the PID to kill the process causign the increase in load. (replace 'PID' with the correct process id #).

```
sudo pkill -9 'PID'
```

If that doesn't help, and you need to reboot.

```

sudo shutdown -r now

```

To log out

```

exit

```

To return to your x session:
ctrl+alt+F7

---

### Post by daltore on 2009-09-17
By the time the load increase starts, it's too late to do ANYTHING software wise.  I can't start or stop programs, and I can't switch to another tty (which is why I have to resort to the hard shut down, I wouldn't do it if there were any other possibility).  I have all of the monitors set to show any increase in usage on ANY account, not just mine, so anything done by the system will show up before it happens.  The issue is, that nothing's happening, the load just starts stepping whether or not processor, memory, SWAP, network, or hard drive are actually being used.

The worst part is, I don't even know a way to force it to happen, so I can't make a specific log, or even find which log to watch.

However, if this has something to do with the issue, Xorg consistently takes up a LARGE percentage of the processor usage, such as 1/3 when on 1.2 GHz, or 2/3 when on 798 MHz (mobile processor).  However, there's still no spike in processor usage, just another issue I've yet to hammer out.  Although, they may well be linked.

---

### Post by daltore on 2009-09-18
Quick update (I know I just posted 20 minutes ago), but I got Xorg to calm down the cliched way, I reduced the color depth from 24 bits to 16 bits, so now instead of sitting at 30% processor usage, it's around 3%, max.  And the slow typing/scrolling issues I was having as a side went away, too.  Something I knew that I hadn't really gotten around to fixing, so we'll see if this solves the load problem too.

---

### Post by daltore on 2009-09-18
So after working well last night after the downshift to 16 bit color depth, I shut it down, and went to bed.  I got up this morning and tried to print something, and it crashed again.  Rebooted, tried again, and it crashed fairly immediately.  Rebooted AGAIN, this time didn't even get to open OpenOffice/Abiword (both crashed it), or pretend like I was going to print anything, and it crashed a third time.  3 crashes in 20 minutes without doing anything intense, on Linux, gotta be a record.  I'm running it on failsafe Gnome right now, and it seems to be running okay.  I disabled most of the startup programs, so we'll see if that helps any.  One of my friends has been having the same problem recently, so tonight we're going to try to diagnose.

---

### Post by daltore on 2009-09-20
So, I managed to force a crash by opening OpenOffice and trying to print a few high-color documents, while recording the top output into a text file, and it looks like python is the culprit.  Working on a fix.

---

### Post by wirelessmonkey on 2009-09-20
Try installing htop:
```
sudo apt-get install htop
```

then run it in a terminal in the foreground until the machine freezes, it will likely show your culprit, and is much easier to read than top.

also, check the output of
```
 dmesg | less 
```
and see what happened right before your reboot.


WM

---

### Post by daltore on 2009-09-27
I may have fixed it.  On a thought, I booted to the generic kernel (instead of the realtime kernel from Ubuntu Studio that I usually use), and then put it through it's paces.  It doesn't lock under my normal methods for inducing a crash, so that may have been the problem.  I'll change it over in menu.lst and boot to that habitually from now on and see if it fixes it.

---

