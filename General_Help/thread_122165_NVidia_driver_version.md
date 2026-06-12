---
title: "NVidia driver version"
date: 2006-01-26
forum: General Help
---

### Post by OPaul on 2006-01-26
How do I tell which NVidia driver version I am using? I'm having trouble getting -vo vx to work in Mplayer (i.e full screen doesn't work) and I can't get the game "Cube" to run (which I was using to test 3D).

---

### Post by o_fortuna on 2006-01-26
[QUOTE=OPaul]How do I tell which NVidia driver version I am using? I'm having trouble getting -vo vx to work in Mplayer (i.e full screen doesn't work) and I can't get the game "Cube" to run (which I was using to test 3D).[/QUOTE]
If you are using the one from the official Ubuntu repositories (ie, you didn't go to NVidia's website and get it yourself, you got it from Synaptic), then the driver version is 7667. The most recent version is 8178 (get it [here]("http://www.ubuntuforums.org/showthread.php?t=75074"))

---

### Post by Jedeye on 2006-01-26
I installed my nvidia drivers using Automatix [http://www.ubuntuforums.org/showthread.php?t=66563]("http://www.ubuntuforums.org/showthread.php?t=66563")
and then I could view all of my video card info by going to applications/system tools/nvidia settings

hope that helps

---

### Post by OPaul on 2006-01-26
Well I've been messing around with it so I don't know which I have installed right now. Is there not a command to tell me?

---

### Post by astoltz on 2006-01-26
Try this:
```
cat /proc/driver/nvidia/version
```

---

### Post by OPaul on 2006-01-26
Thanks

---

### Post by OPaul on 2006-01-26
nevermind

---

