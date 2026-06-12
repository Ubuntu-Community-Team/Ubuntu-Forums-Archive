---
title: "How to install Lubuntu 11.04 from usb drive?"
date: 2011-05-12
forum: General Help
---

### Post by alexandrius on 2011-05-12
Hello everyone,
Recently my disc drive died from unknown reasons :D and because of this i have no other variants of installing Lubuntu except using usb drive.
I tried Unetbootin and usb-creator-gtk non of them worked. The "Try Ubuntu Without Installing" won't load in both situations. :(
Any help?

---

### Post by terarmt on 2011-05-12
I think that is a computer system problem.

---

### Post by coldraven on 2011-05-12
Did you select "Boot from USB drive" in your BIOS?
You have to change the boot order so that it tries to boot USB first.

---

### Post by C.S.Cameron on 2011-05-12
Have you checked the iso MD5SUM to see if the download was corrupted?

---

### Post by Tanasqui on 2011-05-12
My first thought as mentioned above, by C.S.Cameron, check the md5sum with one of the programs listed [here]("http://ubuntuforums.org/showthread.php?t=967665"). 
If your checksum is good, I would suggest [LiLi (linux live usb)]("http://linuxliveusb.com/downloads/?version=stable"). They take an week longer to update for new distributions than other programs out there. But I used a LiLi usb key to install Natty (11.04) last night(actually 5am) and it worked like a champ. 
On boot up don't forget to press F10 (or whatever it is on your system) to view bios options as mentioned by coldraven and select your USB key.
Good luck to you.

---

### Post by cavalier911 on 2011-05-12
If your trying to boot an old processor that doesn't support CMOV instruction set you have to use Lubuntu Lucid 10.04

---

### Post by alexandrius on 2011-05-12
@terarmt i've installed some other distros or older ubuntus with usb flash drive

@coldraven that's not a problem. usb boots up

@C.S.Cameron I don't think so, none of the other downloads worked either

@Tanasqui Lili works on windows not linux, i'm on lubuntu 10.10 now

@cavalier911 Yeah the CPU is rather old but how do i find out if it supports the CMOV instruction set?

---

### Post by alexandrius on 2011-05-12
El Uppinho

---

