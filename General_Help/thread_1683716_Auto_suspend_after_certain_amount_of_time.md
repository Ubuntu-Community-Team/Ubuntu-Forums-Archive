---
title: "Auto suspend after certain amount of time"
date: 2011-02-08
forum: General Help
---

### Post by winchendonsprings on 2011-02-08
Most nights I fall asleep watching tv or movies. I want the computer to go to sleep after I do. Under Power Management Properties I have "put computer to sleep when inactive for 1:00" yes - to " spin down hard disks" and "put display to sleep when inactive for 1:00"

I'd say 65% of the time I wake up and the computer is running, not suspended, and 45% of the time the monitor is still on.

Over the past 8 months or so I have been trying different media players. I tend to have the same problem of the computer not sleeping with all of them. (Banshee, Miro, xbmc, boxee, vlc, totem, )

So...

1. Is there a process I can look for that may be running some of the time that would hinder the suspend function?
2. Is there a simple script I can write for "suspend in 90 minutes"
3. I think I remember seeing way to do this from the CLI with pm-suspend, yeah?

Edit- I found this [http://bit.ly/hpThVM](http://bit.ly/hpThVM) 
Things I tested that didn't work
~$ sudo echo pm-suspend | at 12:27
~$ sudo sleep 30s

---

### Post by winchendonsprings on 2011-02-08
Little bump up. 

Theres gotta be someone here that knows a simple command to Suspend the computer after a set amount of time.

---

### Post by winchendonsprings on 2011-02-09
So if anyone is interested this is what I found that works, and works without having to install anything, and works as non-root.

Use this command
```
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```and to delay it use the sleep command with  a number with either s m h or d (sec, min, day, hour) and with a ;

example
```
sleep 60s; dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```That suspends the computer after 60 seconds

---

### Post by r1ba5 on 2012-05-09
Found a more elegant way:
```
sudo sleep 60s; sudo pm-suspend 
```

---

