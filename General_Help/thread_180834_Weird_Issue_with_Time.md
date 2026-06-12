---
title: "Weird Issue with Time"
date: 2006-05-23
forum: General Help
---

### Post by DiGiTY on 2006-05-23
i just noticed the time in my BIOS was incorrect, 3 hours ahead, so i changed it to the correct current time (i'm in New York, EST, -5). when ubuntu booted, its time now was 3 hours behind the correct time. i change it to the current time and of course the BIOS time was back to 3 hours ahead... so basically ubuntu is doing something screwy with the time when setting it... how do I fix this???

this is important, because I'm developing an app on this machine that's time sensitive

running Flight 7, but i'm sure it's just a ubuntu thang

TIA

---

### Post by Phlosten on 2006-05-23
I think you will find that Ubuntu assumes that your bios is set for UTC time and then corrects for this according to your preferences when you boot into Ubuntu.
This causes issues for Windows which has always set the BIOS time as your actual local time. 
If you are not running a dual-boot I would advise leaving the BIOS at UTC time. I am fairly certain this is the preferred setup for Internet servers and the like. (Someone feel free to correct me).
If you are running a dual boot you may have to do some manual config. Someone else may have more info on this (I don't dual-boot)

---

### Post by DeadEyes on 2006-05-23
Maybe [this]("http://ubuntuguide.org/#troubleshooting") might help, see section about "disable system time/date from being reset"

---

### Post by DiGiTY on 2006-05-25
nope, i don't dual boot

thanks DeadEyes, worked like a charm

but now i wanna run a time server (NTP) on this ubuntu machine for just my local home network. should i keep the BIOS time as UTC as suggest still?

TIA

---

