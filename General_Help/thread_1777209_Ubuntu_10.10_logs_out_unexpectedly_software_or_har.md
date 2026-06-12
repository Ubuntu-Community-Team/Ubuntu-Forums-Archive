---
title: "Ubuntu 10.10 logs out unexpectedly: software or hardware problem?"
date: 2011-06-07
forum: General Help
---

### Post by Matematik on 2011-06-07
My laptop Dell Inspiron 1420 running Ubuntu 10.10 has started logging itself out every 30-60 minutes or so. I am trying to figure out what is the problem. I am wondering if it is

1) a hardware problem. I have recently **replaced the cooling fan** which required disassembling the whole thing into small pieces. The computer has worked without a problem for one day after the repair.

or

2) a problem with a **recent update**. The computer started logging itself out after a recent update. This coincidence is suspicious, but I hasn't noticed anyone reporting a similar problem with Ubuntu 10.10.

**Is there a way I can see what is happening through the system log?** What would be the keyword I should look for in the log files?

**Can I track the last updates I have applied and roll them back?**

The only solution I see now is to reassemble the laptop to see if it helps.

Any suggestions are appreciated!

---

### Post by collisionystm on 2011-06-07
Logging out? Is the computer going through a full reboot? If its not doing a full reboot, its PROBABLY not hardware.

---

### Post by Matematik on 2011-06-07
Yes, the computer goes to the log in screen unexpectedly. As far as I can tell the problem occurs independently of the programs I'm running.

---

### Post by FormatSeize on 2011-06-07
I wish I could be of more help, but I can only offer a few suggestions from my past experience.
 
I wouldn't disassemble and reassemble the computer, because it is likely not a hardware problem. If your fan was problematic and the computer felt uncomfortable (no pun intended), then the computer would completely shut off before it even had a chance to go through the logout process. I've had problematic cooling issues on laptops before. 
 
The last time that I had Ubuntu 10.10 log me out when I didn't expect it was when I built a machine from the ground up, and in using cheap parts because it was my first build, I plugged in a decrepit video card (not being too big on hardware at the time, I didn't know the difference between a video card and a graphics card), and then went to go adjust the monitor settings. I would go into the monitor menu, then the next thing I knew I was logged out. 
 
Not saying that your hardware is bad like mine was, but is there something in particular that you are doing when it is logging you out, or does it just happen?
 
Lastly, and this one is rather hilarious now that I think back on it, occasionally in conference rooms people are mysteriously logged out. That's because the conference rooms are equipped with wireless keyboards so that you don't have to actually sit in front of a computer to show things on the projector during a meeting. Well, if the battery is low on the keyboard, it logs you out whenever you push the "l" key. I haven't a clue whether there is a technical term for this phenomenon or not, or why it happens, all I know is that if the battery is low, then you will be logged out unless you don't need the "l" key.
 
So to apply that to your situation, is your laptop plugged in to a wall when this happens? If not, then perhaps your battery needs replacing.

---

### Post by collisionystm on 2011-06-07
the actual login screen, or a the lock screen? Does it have a black background and a login box?

---

### Post by Matematik on 2011-06-07
**FormatSeize**: Thanks for your suggestions. The log out can happen even if the computer is idling. When I work on the computer and the problem occurs I first see a black screen and then a log in screen. As for the wireless devices, I only use a wireless mouse I've always used, so I don't think I started to use some new hardware that triggered the problem.
[B]
collisionystm[/B]: I get to the log in screen, not the locked screen. All the applications are getting closed.

---

### Post by Matematik on 2011-06-08
The problem seems to be due to the recent upgrade of the Linux kernel in  Maverick (dpkg.log says it's been upgraded from 2.6.35.29.37 to  2.6.38.10.24). I've found that the following messages might be related  to the X server crash:
```

/var/log/daemon.log:Jun  8 10:25:19 zver gdm-session-worker[7304]:  WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or  directory
/var/log/kern.log:Jun  8 10:25:16 zver kernel: [55707.291313]  [drm:i915_gem_object_bind_to_gtt] *ERROR* Attempting to bind a purgeable  object
/var/log/syslog:Jun  8 10:25:16 zver kernel: [55707.291313]  [drm:i915_gem_object_bind_to_gtt] *ERROR* Attempting to bind a purgeable  object
/var/log/Xorg.0.log:[ 56031.956] (WW) intel(0): i830_uxa_prepare_access: gtt bo map failed: Invalid argument
```

A similar bug has been reported at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/682712](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/682712)

I would really appreciate if anyone can give some hints.

---

