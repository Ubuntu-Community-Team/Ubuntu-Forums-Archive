---
title: "Alsa Nforce 4 Help"
date: 2006-06-06
forum: General Help
---

### Post by spockrock on 2006-06-06
Ok I have an nforce4 board (DFI NF4 Ultra-D) I am sure the alsa drivers are loaded as I see intel 0x80 (the alsa driver needed to install for the nforce boards) when I lsmod.

however it seems only one application can use sound at a time, I thought that was oss behavior and I should hear sound from multiple programs......

I cannot find asound.conf in /etc or in my home folder. 

I havent installed nvidias binary drivers.  Can anyone help me out.... its annoying  having to restart swiftfox everytime I wanna watch flash.

---

### Post by garyng on 2006-06-06
it is ~/.asoundrc or /etc/asound.conf

my nforce2 doesn't have mixer so I need use the software mixer for multiple simultaneous in/out. don't know about nforce4

---

### Post by spockrock on 2006-06-06
ok I dont have .asoundrc in home.

and what software mixer are you using, and how do I use it as well??

---

### Post by spockrock on 2006-06-07
anyone on how to use the software mixer??

---

### Post by panurge77 on 2006-06-07
$alsamixer

---

