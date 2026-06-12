---
title: "K3B hangs after ripping CD"
date: 2011-09-25
forum: General Help
---

### Post by ofnuts on 2011-09-25
At the end of a CD rip, K3B won't close. To be accurate, I have:

- a small window without decorations saying "Ripping audio racks from ..." which remains above all other windows (K3B and other) and won't move
- a medium size window titled "(100%) ripping audio tracks from...". Both progress indicators are at 100%, the track list won't scroll, and clicking the "Cancel" button doesn't elicit an action, and clicking the close button on the titlebar gert me a "window not responding" dialog.
- the main K3B window is completely unresponsive (won't even refresh its contents)

- my CPU indicator and task monitor show that K3B is running full blast on one CPU

This is version K3B 1.91.0 (standard Lucid Lynx issue). 

Known problem? Worth getting a more recent version?

---

### Post by ron999 on 2011-09-25
> **ofnuts said:**
> 

This is version K3B 1.91.0 ... Worth getting a more recent version?
Yes, a later version is available for lucid:- [http://packages.ubuntu.com/lucid-backports/k3b]("http://packages.ubuntu.com/lucid-backports/k3b")

---

### Post by ofnuts on 2011-09-25
> **ron999 said:**
> Yes, a later version is available for lucid:- [http://packages.ubuntu.com/lucid-backports/k3b](http://packages.ubuntu.com/lucid-backports/k3b)OK, thanks. I assume I must first uninstall V1.91?

---

### Post by ron999 on 2011-09-25
Hi
First enable 'Unsupported updates (lucid-backports)'.

Look in:-
System > Administration > Software Sources > Updates

Then:-
```
sudo apt-get update && sudo apt-get install k3b libk3b6-extracodecs
```

---

### Post by ofnuts on 2011-09-25
> **ron999 said:**
> Hi
First enable 'Unsupported updates (lucid-backports)'.

Look in:-
System > Administration > Software Sources > Updates

Then:-
```
sudo apt-get update && sudo apt-get install k3b libk3b6-extracodecs
```
Upgraded to v2 and still the same problem... the aggravating part is that it won't save the ripping options so I have to reenter them each time.

I'm wondering if it could be a device access problem. After a while I ejected the CD, hoping it would cause an error in k3b and wake it up, but it did nothing... but when I inserted another CD the system didn't react as usual. Is k3b trying to eject the CD but failing?

---

### Post by ofnuts on 2011-09-25
Actually looks like [it's a bug fixed in... 2.01.]("https://bugs.kde.org/show_bug.cgi?id=236466") The fun part is that it comes from the debug code and occurs only when debug output is disabled, so developers had a hard time figuring it out.

---

