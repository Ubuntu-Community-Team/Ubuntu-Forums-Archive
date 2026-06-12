---
title: "Compiz enabled Sluggish, but can run 3D games."
date: 2009-11-25
forum: General Help
---

### Post by leveliv on 2009-11-25
I can run 3D games like Doom 3 and all the other shooters and games that require Nvidia drivers.

However when I enable Compiz or "Desktop Effects" my computer is sluggish as hell and I can't get rid of it until I log out and goto into Xterm and remove Compiz. 

This doesnt make any sense I have ran compiz on another PC running 1.3Ghz cpu and 512 ram plus an old AGP graphics card and it ran fine. 

this PC has a 2.3 ghz CPU and 1 gig ram and a newer PCI E card.

also im running the 185 Nvidia drivers on 9.10

---

### Post by lidex on 2009-11-25
Try this. Go [here]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html") and install 190.xx drivers. Keep us updated ;)

---

### Post by leveliv on 2009-11-26
Installing them now, Hopefully they work.

---

### Post by leveliv on 2009-11-26
That didn't help at all, At least I got them to update. 

This is really puzzling.

---

### Post by lidex on 2009-11-26
Did you reboot? BTW you're using jockey, right?
Can you post output of
```
lshw -C video
```
and
```
compiz --replace
```
run this last
```
dmesg | tail -n 40
```

---

