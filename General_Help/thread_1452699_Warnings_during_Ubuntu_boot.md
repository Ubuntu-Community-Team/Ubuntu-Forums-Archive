---
title: "Warnings during Ubuntu boot"
date: 2010-04-12
forum: General Help
---

### Post by kr0n1x on 2010-04-12
Hi, during my Ubuntu (9.10 64 bit) boot I see many "WARNING: blabla, IGNORED" lines.

Checking in "dmesg" into my terminal doesn't help me, because it doesn't show me those warnings...

I've tried looking in my System Log Wiever (in System/Admin menu) but no traces of these warnings :(

Also, I think my ubuntu time is very long (1m 30s), considering I've a not-very-old pc:
core 2 duo e6300 (1,86ghz)
2*512mb ddr2 800mhz (dual channel)
ext 3 file system (i don't format my ubuntu installation since... i think 8.04)

How can I see what causes those warnings and how can I improve my boot time?

Searching on google, I've found bootchart. Would a .png of that software help you?? If yes, could I post the .png file how is it? Or have I to hide something (important/private info)?

Thank you, bye!

---

### Post by kr0n1x on 2010-04-14
anyone who can help me? :confused:

---

### Post by dannyboy79 on 2010-04-14
have you removed the words "splash quite" from your grub boot line? when ubuntu it booting up, get into grub, edit the kernel your booting, then edit the boot line, at the end it will have quite splash, remove them both and you see a lot of messages as it's booting. very strang though that the messages aren't in dmesg as from my understanding that contains the boot log. have you checked kern.log?

---

### Post by kr0n1x on 2010-04-15
i've removed quiet and splash from the boot line in menu.lst

the boot time is till around 1.30, i saw more messages ofc... because i had no splash anymore... and i saw again the various warnings

no trace of these warnings in kern.log, nor into others log files.

i've noticed that these warnings tell something about /etc/modprobe something like that... i don't have the time to read it better :(

also, often times my mouse doesn't work at the login screen, neither after the login. i have to unplug and plug it into my usb port to make it work.

only few times it DOESN'T happen.

this is my last bootchart .png: [http://img52.imageshack.us/img52/4081/conroe6300karmic2010041.png](http://img52.imageshack.us/img52/4081/conroe6300karmic2010041.png)

---

### Post by dannyboy79 on 2010-04-16
well hal was removed and something took it's place. i was guess that the warnings and your mouse not working, they're related. are you all up-to-date? after you boot up, can you go to tty1, and log in, then do 
sudo apt-get update && sudo apt-get upgrade

then see if you still haev this issue.

---

### Post by kr0n1x on 2010-04-30
> **dannyboy79 said:**
> well hal was removed and something took it's place. i was guess that the warnings and your mouse not working, they're related. are you all up-to-date? after you boot up, can you go to tty1, and log in, then do 
sudo apt-get update && sudo apt-get upgrade

then see if you still haev this issue.

many times my keyboard and mouse don't work when the login screen comes up.
sometimes i've to plug off and on my mouse to make it work, and sometimes it doesn't work completely (like if the computer would be freezed... and probably it is)
it happens MANY times

when ubuntu loads up correctly (i mean i can use keyboard and mouse at login screen) i can go to tty1 and login and update etc... yes i can

---

