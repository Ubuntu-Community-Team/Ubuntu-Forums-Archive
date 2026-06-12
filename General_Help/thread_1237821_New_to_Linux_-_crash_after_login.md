---
title: "New to Linux - crash after login"
date: 2009-08-11
forum: General Help
---

### Post by Captcol on 2009-08-11
Hardware

old reclaimed pc
AMD Duron 1100mhz
512mg pc133 ram
20gig ide hdd
Motherboard - can't see the model atm but uses via chipset and I think i recall seeing s3virge for the onboard graphics.

The issue.  I first install ubuntu 9.04 and would get a crash after logging in from the grahpical login, complete system lockup on the blue background with the mouse arrow frozen on screen, caps lock doesn't respond.

So I figured maybe the system doesn't have enough grunt, researched the forums disable compiz and some other packages to no avail

I then installed xubuntu seeing that it was for lower end systems, the same issue happened.  I then decided to try a different approach as it may be the mouse or keyboard.  Eventually I found a command that listed the usb devices and the keyboard and mouse were listed correctly and mx revolution and logi keyboard.  I had tried with ps2 keyboard and mouse same issue.

So now I am here after trying multiple suggestions on how to fix a unresponsive mouse and keyboard.  The only reason I am still battling this on this hardware is becuase once and only once I sat here and played with the mouse while it was logging in and it got to desktop, I celebrated and shutdown my laptop so i could concentrate on playing on my new ubuntu machine and it crashed.

How can I proceed from here, how do I identify what the issue is
I have run apt-get upgrade etc and I am told that all packages apart from 4 being held back are the latest and greatest.

Even Alt+Sysreq REISUB has no effect at this point

I can login at tty1

Please any advice would be appreciated

Colin

---

### Post by Captcol on 2009-08-11
Just attempted the below from tty1 login

> 
How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:

Code:
```
sudo /etc/init.d/gdm stop 
```(or kdm for KDE)You can do the whole X configuration process by entering:

Code:
  ```
sudo dpkg-reconfigure xserver-xorg
```


This resulted in a 


```
[   352.395212] kernel panic - not syncing: Attemped to kill the idle task!
```

---

### Post by AliTabuger7 on 2009-08-11
What does your /var/log/Xorg.0.log look like?

I suspect that it must have something to do with X.org, like you're already thinking.

Did this happen after you installed restricted drivers, or did you not get to try that?

---

### Post by Captcol on 2009-08-11
I didn't get to try that,

now i will research how to find and see the logs, gives me something to go on at least.

---

### Post by Captcol on 2009-08-11
most recent log complains of

no core pointer or keyboard, if no devices come available recongigure HAL

Identifies video as Savage

Seems to spend along time choosing the resolution to run, and testing every conceivable combination or Res, Refresh, vsync and hsync

Says vid ram is sufficient for 3d - I was surprised at that

Sets up generic mouse then last line of log reads

```

(II) AIGLX: Suspending AIGLX clients for VT switch
```

didn't seem to be any areas apart from above, will check the old log to see if there is any glaring differences

Xorg.0.log.old finishes a line earlier from what i can see on
```

(**) PS/2 Generic Mouse: (accel) set acceleration profile 0
```

**New information** after reading through the logs I switched back to the gui login, logged in and get a out of range message from my monitor this is a new and exciting development that apparently by reading the logs has altered the behaviour ...

This would lead me to believe that it is a Xorg issue... I think

Just now while in console I got a kernel panic lock up, think the whole install is borked, might try a fresh shot at it

---

