---
title: "black screen after booting up"
date: 2009-08-28
forum: General Help
---

### Post by selectstar on 2009-08-28
Hi there, I can't use my laptop with Ubuntu 9 installed.
2 nights ago I done an update of the software and after that it was asked me to reboot the system
once the system booted up I started to see a black screen with the mouse cursor in the middle of the screen
the cursor moves if I move the mouse
after a few minutes I can hear the short  music of when Ubuntu loads up.
and then nothing else happens apart from the black screen and the cursor that moves when I move the mouse.

what can it be???

---

### Post by bchurchill on 2009-08-28
Can you still boot into recovery mode fine?  How about accessing the TTYS after booting normally?  (press CNTL+ALT+F2)

If you can get access try looking in the following places for clues, and post information that looks relevant:

cat /var/log/syslog
cat /var/log/dmesg
cat /var/log/Xorg.0.log

and if you're at a tty after a normal boot you could also try doing:

ps -e | grep gnome 

or perhaps

sudo /etc/init.d/gdm restart

---

### Post by selectstar on 2009-08-30
Recovery mode works fine

also if use CTRL + ALT + F2 it works fine

I don't have | character on my keyboard and I have tried with CTRL + shift + U7C but it doesn't type it so I can't run 
ps -e | grep gnome 

with 
sudo /etc/init.d/gdm restart
I get back exactly from the starting stage: black screen and mouse cursor

---

### Post by selectstar on 2009-08-30
I don't know it this can be related
When I go in recovery mode and I select the recover disk option
the scan starts and loads of errors are found:

"I/0 error, dev sda, sector 52.... error reading block (attempt to read block from filesystem in shor read) while gettint next inode from scan.  Ignore <Y>"

---

### Post by bchurchill on 2009-08-30
> **selectstar said:**
> I don't know it this can be related
When I go in recovery mode and I select the recover disk option
the scan starts and loads of errors are found:

"I/0 error, dev sda, sector 52.... error reading block (attempt to read block from filesystem in shor read) while gettint next inode from scan.  Ignore <Y>"

Yeah, that would be a problem.  It could be that several files on your disk are corrupted, or maybe that your disk is failing in places.  If you have a recent backup, this would be a good time to restore.  Otherwise, reconfiguring X might work.  From recovery mode or a tty, try running

sudo dpkg-reconfigure xserver-xorg

and follow the directions.  This will (hopefully) solve your problem if the issue is that X has lots its configuration files.  If more files have been corrupted it probably won't help much.  Reboot when you're done.

---

### Post by selectstar on 2009-08-30
thanks bchurchill
bad news, I even couldn't attempt to follow your advice
now I boot up everything blocks and it tells me to perform an fsck
I run the fsck but I start to get loads of those error messages and keep pressing "Y" key to "ignore" the warning and keep performing the scan.

I will never be able to escape all those warnings... unless I do like homer simpson and put a bird that keeps pressing the same key :)

in any case this really seems to be an hard drive problem, so maybe it doesn't have much to do with Ubuntu?? :confused:

---

### Post by jheaton5 on 2009-08-30
I agree that this is a hardware issue.

---

