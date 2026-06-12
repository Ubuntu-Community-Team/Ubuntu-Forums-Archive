---
title: "irrecord lockups up on ubuntu 10.4"
date: 2010-05-08
forum: General Help
---

### Post by carpet_pants on 2010-05-08
Hi everyone, Ive installed ubuntu 10.4 x64 on my desktop machine. I am running mythtv and trying to setup lirc but irrecord does not want to work for me. So Im using a marmitek x10 wireless remote control which uses the lirc_atiusb driver. I have modprobe the driver and can see an entry in /dev/lirc0.

Everything seems ok so now I want to record a new config since mine from fedora 12 doesnt seem to work. I have started lircd as follows:

sudo lircd -n -d /dev/lirc0

in another terminal I have started irrecord

sudo irrecord -d /dev/lirc0 lirdcd.conf

irrecord starts with the welcome message and I press enter. It then asks me to hold down an arbitary key, so I hold a key on my remote and see the dots progressing across the screen. Next it asks me to enter the name for the next button. I enter the button name that is in the namespace i.e. BTN_1 and irrecord doesnt do anything. The cpu on the machine ramps up to 100% and I have to kill the process.

Help does anyone have any ideas whats wrong. I know my remote works and I know lirc can see it, so whats up with irrecord! aagghh

---

