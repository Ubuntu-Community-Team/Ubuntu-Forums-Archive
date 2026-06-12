---
title: "(LUCID) Not able to switch active windows"
date: 2010-05-13
forum: General Help
---

### Post by Dvorakis on 2010-05-13
I just recently installed ubuntu lucid. I have had a decent amount of experience with ubuntu, but this problem is killing me.
When I boot up, everything seems to work fine( The plymouth screen doesn't work, but I hear thats a fault of my Nvidia card)  It boots into the desktop and all appears well. The problem is, when I open a window, or if a window opens, then that one active window is the only windows I can click on(Note that I cannot click on the top panel to close min or maximize the window, or even move it) The only way I can change this is if I alt-f4 to get out of the program. Sometimes as well, I can't even click on the system panel! They cursor always moves, and hotkeys work fine, but I can't do anything efficiently.  Sometimes however, everything works for a couple of click, but then goes back to the same old problem.

Another problem-I have trouble running updates because it can't Grab my mouse, which I imagine is a problem stemming from this one.

EDIT: I just found out that right clicking on the active area sometimes gives me some normal control.. If that helps.

Any help, please reply if you need more info. I would really love to fix this one.

---

### Post by Dvorakis on 2010-05-14
Does Nobody know how to help, its basically preventing me from using ubuntu.

---

### Post by thomas144 on 2010-05-14
I'm not an expert on Ubuntu...but  I might be able to help.  I'm thinking you might be able to temporarily bypass this problem by  using Alt + Tab to switch windows. For a more permanent fix, your can install a driver. Go to System > Administration > Hardware Drivers. What do you see?

---

### Post by cbecker78 on 2010-05-14
try opening a terminal or alt+F2 and typing "metacity --replace"

If that doesn't work, installing a new window manager may fix the problem for you... but the fact that you are having issues with the gnome panel too suggest that the issue may be bigger than just the window manager.  Also go and disable all desktop effect in compiz... now see if it works (you may want to reboot).

So try the metacity --replace command, disabling effects, and if that doesn't work, maybe post the output of "top"...

---

### Post by Dvorakis on 2010-05-16
Sometime, doing metacity --replace fixed the problem for about 5 seconds.

But only sometimes. I've tried disabling compiz completely and theres no help.

Also, alt-tab doesn't do anything.

---

### Post by cbecker78 on 2010-05-16
what's your cpu usage like?  Can you post the results of "top -n 1"

You could also try installing another desktop environment like kde or xfce  "sudo apt-get install kubuntu-desktop" or "sudo apt-get install xubunt-desktop"... then log out, switch to one of those and see if you have better luck.

---

### Post by Dvorakis on 2010-05-17
>  top -n 1

top - 16:16:01 up 2 min,  2 users,  load average: 1.21, 0.91, 0.36
Tasks: 247 total,   1 running, 246 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.9%sy,  0.0%ni, 83.3%id, 15.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4102880k total,   499232k used,  3603648k free,    23624k buffers
Swap:  6384632k total,        0k used,  6384632k free,   224984k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      20   0  2796 1644 1200 S    0  0.0   0:00.85 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.35 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.20 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/3        
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4        
   16 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/4        
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/4         

This is what I get running that command. I'll try the different desktop environments in a bit.

EDIT: Currently running KDE without a hitch.
What gives? I'd rather be using a Gnome environment.

---

### Post by cbecker78 on 2010-05-18
cpu usage looks pretty clean, though the wa (% time cpu is waiting on an i/o process to finish) is kinda high.  Were you downloading or transfering/copying files when you ran that command?  If not, it could be some corrupt part of gnome/metacity that is causing the i/o wait.

In any case, since you are running w/o a hitch in kde, this indicates the problem is isolated to your gnome desktop.  best bet is to remove the ubuntu-desktop and reinstall fresh. (ubuntu-desktop only affects gnome)

You might try running "sudo apt-get -f install ubuntu-desktop" first and see if that works. otherwise, boot up with a live cd, copy your entire home directory over to a usb, then follow this guide to prepare a list of installed packages so you can get your installed software back: 
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Then run "sudo apt-get remove ubuntu-desktop" then "sudo apt-get purge ubuntu-desktop" then "sudo apt-get install ubuntu-desktop"... that should give you a fresh ubuntu-gnome environment.  When you copy your home back into the new gnome, you should get all of your settings back (if they went away).  Since I've only run those commands on a relatively fresh install, I don't know if they remove gnome settings or not.  But I think they do.

You might want to start a new post on how to remove and reinstall gnome desktop in ubuntu to get some other commentors to confirm the above, just to be safe.  Good luck!

---

### Post by zami on 2010-05-18
Dvorakis - are you on a laptop by chance?

I have this problem all the time on my netbook.  If I switch to the thumbpad and just wiggle the cursor, all returns to normal.  

Sorry if it doesn't apply at all.  Darn easy work-around if that *is* the problem though. 

-zami

---

