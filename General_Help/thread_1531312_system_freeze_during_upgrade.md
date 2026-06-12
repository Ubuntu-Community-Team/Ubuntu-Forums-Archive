---
title: "system freeze during upgrade"
date: 2010-07-14
forum: General Help
---

### Post by tonytraductor on 2010-07-14
I'm putting this in general, because I'm not sure if many of the specifics are relevant.
I have an everex cloudbook which I purchased from eBay with hardy herron on it.
I finally got around, today (I've had it for a year), to installing netbook remix 9.10 with a usb key I had also purchased from eBay.
Now, during the upgrade (using update manager) from 9.10 to 10.04, the system appears to have frozen.
(desktop frozen, no response to keyboard or mouse).
Now, I'm not sure if something could still be happening inside there, and if it would be a good idea to let the machine site overnight before rebooting it.
Frankly, it happened once already, and I rebooted, and update manager just took up where it left off once I logged in.
I have not determined what's causing these freezes.
It's not a new machine, of course (everex, afaik, doesn't even exist now), so maybe netbook-remix is too taxing on the hardware?
I installed xfce to get away from the bloated netbook-remix graphical menu garbage, which did seem to allow the system to run faster.
Anyway, the real question here is, while the interface appears frozen, could the upgrade still be developing under the surface?
(I hear a fan running in there.  There is no hdd to spin, but flash memory, so I don't know if the fan is any indication of internal activity).
Would you wait to reboot it? (update mgr indicated 4 hrs remaining to upgrade, in the installing upgrades phase, not downloading, appears it froze during "Running post-installation trigger install-info").
Or just reboot it and see what happens (get update mgr to start again?)?
The system never froze on me with hardy.  It was pretty quick and snappy, in fact.

---

### Post by tonytraductor on 2010-07-14
Okay, at this juncture, I decided to go ahead and try to reboot.
Several times it got to "checking battery state   [OK]", and just stopped, for a really long time.
I'm going to reinstall 9.10, and not upgrade to 10.04.

---

### Post by tonytraductor on 2010-07-14
Actually, I've decided to boot to terminal (ctrl-alt-f1) and run 
dpkg --configure -a
and see if that fixes anything.
I'm kind of wondering, still, if the upgrade to 10.04 was real smart, considering it's apparently a real resource hog (recommended 1gb ram minimum?  
My other laptop is a 750mhz ibm a21m thinkpad with 512mb ram, and still runs jaunty lightning fast...probably won't be upgrading that one soon...At the moment, I don't recall how much ram this everex cloudbook has, but, iirc, it has more cpu and ram than the thinkpad).

---

### Post by tonytraductor on 2010-07-14
dpkg --configure -a is running now.
I think it should fix the 10.04 install to boot, at least.
Not too sure if it's going to do anything useful in respect to these system freezes, though.

---

### Post by tonytraductor on 2010-07-14
OMFG.
Okay, dpg --configure -a got 10.04 "repaired", and I was able to boot it, but it is completely useless.
If I boot to a netbook-remix session, the interface is completely garbled (fonts completely unreadable, etc.)
If I boot to gnome, one after another, infinitely and indefinitely, "starting file manager" appears in the task bar, as if the machine is starting the file manager 3 million time, CPU usage goes through the roof, and the machine is unusable.
The XFCE that was working so nicely with 9.10 has a panel the size of the entire desktop, so nothing else can be seen, and running openbox doesn't give me access to the network applet to start the wifi.
10.04 is a nightmare.

---

### Post by Slade Winstone on 2010-09-20
Everex Cloudbooks, or Step Notes or whatever else they were marketed as, are a COMPLETE nightmare.

Everybody had terrible lockups with them.  Mine has been sitting on a shelf for 9 months.

I recently saw this post where there is a report of good success running Debian on the cloudbook, so I'm going to give it a go.

[http://tonytraductor.livejournal.com/298691.html](http://tonytraductor.livejournal.com/298691.html)

Good luck,
Slade.

---

