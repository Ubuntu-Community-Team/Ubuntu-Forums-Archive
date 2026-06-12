---
title: "DVD cannot read from source"
date: 2009-12-25
forum: General Help
---

### Post by DrScum on 2009-12-25
Using Ubuntu 9.04 DVD was working until the last upgrade. Using VLC-Player, Movie Player and M-Player, DVD's don't work anymore. 
I can open the DVD with VLC and select the language then it starts playing the copyright warning message and hangs at about 50%.

The DVD appears on the desktop with the correct title upon inserting into the drive and I can browse the drive. 

Any help would be greatly appreciated.

---

### Post by Junkieman on 2009-12-30
Hi. Do you restricted extras installed? I know it sounds like you do since it does play some of the movie, but just in case, add the [medibuntu repository as shown here]("https://help.ubuntu.com/community/Medibuntu"), then you can install the DVD decoder package like so:

```
sudo apt-get install libdvdcss2
```

This worked for me, good luck :)

---

### Post by dantakeoff on 2012-11-11
> **Junkieman said:**
> Hi. Do you restricted extras installed? I know it sounds like you do since it does play some of the movie, but just in case, add the [medibuntu repository as shown here]("https://help.ubuntu.com/community/Medibuntu"), then you can install the DVD decoder package like so:

```
sudo apt-get install libdvdcss2
```

This worked for me, good luck :)

Dude thanx

---

