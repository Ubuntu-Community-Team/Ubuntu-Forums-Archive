---
title: "Getting computer info ?"
date: 2010-07-10
forum: General Help
---

### Post by Cpierce on 2010-07-10
Guys, I am sure there is a program or command that will give all the computer's info. I am looking for processor type and speed, type of RAM, sound cards, etc.....

Any help is greatly appreciated

---

### Post by Cpierce on 2010-07-10
I just found sysinfo, so never mind.

---

### Post by Steve Kinney on 2010-07-10
In a command terminal do either:

sudo lshw > ~/Desktop/hardware.txt

or 

sudo hwinfo > ~/Desktop/hardware.txt

This will write your hardware info to a text file on your desktop.

---

### Post by Steve Kinney on 2010-07-10
Just installed and tried sysinfo, it works but the commands mentioned above seem to give a lot more detail.

---

