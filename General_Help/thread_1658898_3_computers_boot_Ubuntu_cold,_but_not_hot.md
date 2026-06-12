---
title: "3 computers boot Ubuntu cold, but not hot"
date: 2011-01-03
forum: General Help
---

### Post by jrnsr on 2011-01-03
I have three Dell 2650 laptops and have put both Ubuntu and Xubunt on the HDD. If the computers are cold, they stand a decent chance of booting up, but when trying to reboot when warmed up, they reboot to a frozen desktop; nNo touchpad and usually (not always) locked keyboard.  Have tried USB mouse and no different.  They run flawlessly when 

I tried loading Fedora, but it freezes up on the first installation screen.

Any hints?    ...besides never shut it down?

---

### Post by seawolf167 on 2011-01-03
Do they ever spontaneously shutdown?

The first thing I'd try is using a can of compressed air and blowing all the dust out of the fans and seeing if that helps cool the computer.

If that doesn't work, the next thing I'd do is install hddtemp

```
sudo apt-get install hddtemp
```

then run (in a terminal)

```
sudo hddtemp /dev/sda
```

but change sda to your hard drive designation. The temperatures shouldn't be above ~55C, and should usually be right around ~45C

---

### Post by jrnsr on 2011-01-03
They'll run forever once started, no shutdowns.  It isn't an overheating issue, especially since it is all three computers.

If I boot up successfully, and immediately reboot, it comes back frozen while the computer is still plenty cool.

---

### Post by no2498 on 2011-01-04
If I boot up successfully, and immediately reboot, it comes back frozen while the computer is still plenty cool.

this looks to be a update manager

as far as all 3 
? they all plugged in the same power source ( same room ) house breaker 
may be getting ready to trip
not giving full power

---

### Post by dcstar on 2011-01-05
> **jrnsr said:**
> I have three **Dell 2650 laptops** and have put both Ubuntu and Xubunt on the HDD. If the computers are cold, they stand a decent chance of booting up, but when trying to reboot when warmed up, they reboot to a frozen desktop; nNo touchpad and usually (not always) locked keyboard.  Have tried USB mouse and no different.  They run flawlessly when 

I tried loading Fedora, but it freezes up on the first installation screen.

Any hints?    ...besides never shut it down?

Ancient hardware dating back to 2002 with unsupported Nvidia video chips is always going to be problematic using modern OSs.

Find a distro from 5 years ago and it may work better.

---

