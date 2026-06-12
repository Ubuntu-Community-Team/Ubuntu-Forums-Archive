---
title: "Firefox won't start"
date: 2009-08-06
forum: General Help
---

### Post by bcn17 on 2009-08-06
I was in the middle of an update when I highlighted 14 songs and accidentally played them all at the same time using vlc. (totem just puts them in a playlist) This caused ubuntu to freeze up. After a reboot, and another reboot firefox will not start. I get the little thinking swirl for a couple seconds then nothing happens. 

I have tried sudo aptitude autoclean, and then safe-upgrade and full-upgrade just to try and maybe redo any failed updates but it never did anything so apparently aptitude thinks everything is fine.

- It was during the installation phase of the updates, and firefox was one of the updates, but I don't know if it was installing firefox updates specifically at the time.  

If I type "firefox" into the terminal I get the output "Bus error"

---

### Post by dcstar on 2009-08-06
> **bcn17 said:**
> I was in the middle of an update when I highlighted 14 songs and accidentally played them all at the same time using vlc. (totem just puts them in a playlist) This caused ubuntu to freeze up. After a reboot, and another reboot firefox will not start. I get the little thinking swirl for a couple seconds then nothing happens. 

I have tried sudo aptitude autoclean, and then safe-upgrade and full-upgrade just to try and maybe redo any failed updates but it never did anything so apparently aptitude thinks everything is fine.

- It was during the installation phase of the updates, and firefox was one of the updates, but I don't know if it was installing firefox updates specifically at the time.  

If I type "firefox" into the terminal I get the output "Bus error"

Rename the .mozilla folder and start up Firefox, that will create a fresh profile.

---

### Post by bcn17 on 2009-08-07
> **dcstar said:**
> Rename the .mozilla folder and start up Firefox, that will create a fresh profile.

I tried but it didn't work, thank you anyway.

```
mv .mozilla .mozilla_OLD
```

```
ls -a
```

.mozilla_OLD is present and .mozilla is not.

```
firefox
```

"Bus error"

```
ls -a
```

.mozilla is still not there, it has not been remade, apparently the problem is very early in the chain of events starting firefox

---

### Post by bcn17 on 2009-08-07
FIXED

thread on topic already posted...

[http://ubuntuforums.org/showthread.php?t=1141895](http://ubuntuforums.org/showthread.php?t=1141895)

if you 

```
sudo aptitude remove firefox-3.0
```

and then 

```
sudo aptitude install firefox-3.0
```

this does not fix the problem

you must remove xulrunner-1.9 and nspluginwrapper as well. 

Maybe only 1 of them but I just removed all 3, then reinstalled all three and i was back. Furthermore, my addons, and even tabs were saved. YAY!

---

### Post by bcn17 on 2009-08-07
The mark thread as solved button is gone.... This is very anti-climactic...

---

### Post by Darthnix on 2009-08-07
I can't seem to remove xulrunner-1.9. I get a message telling me that it hasn't been configured yet. This problem is actually causing gnome to crash upon bootup. Anymore suggestions?

---

### Post by dcstar on 2009-08-07
> **Darthnix said:**
> I can't seem to remove xulrunner-1.9. I get a message telling me that it hasn't been configured yet. This problem is actually causing gnome to crash upon bootup. Anymore suggestions?

```
sudo dpkg-reconfigure xulrunner-1.9
```

---

### Post by Darthnix on 2009-08-07
/usr/sbin/dpkg-reconfigure: xulrunner-1.9 is broken or not fully imstalled

---

### Post by bcn17 on 2009-08-08
The thread that gave me advice said to remove xulrunner, I typed ```
sudo aptitude search xulrunner
```

Then because there was an "i" on the left hand side of xulrunner-1.9 I knew that was my version. You might have a different version. Do a search and then make sure to remove and install the exact version you have installed.

---

