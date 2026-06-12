---
title: "Ubuntu+backtrack+grub woes!!"
date: 2010-02-07
forum: General Help
---

### Post by HH60Gunner on 2010-02-07
Hello everyone,

I have one little problem.  I have been running windows 7 and ubuntu until just about a week ago.  I decided I wanted to play around with backtrack 4 as well.  So I made some space and installed backtrack 4.  All went well and grub recognized all 3 OS's.  However after today when i just updated the new ubuntu kernel it doesn't show up in the grub boot menu.  From the looks of it, the grub being used is the one installed from backtrack 4.  I tried to do an update-grub but it still doesn't find the new updated ubuntu kernel.  How do I get it so it will see the new ubuntu update?

---

### Post by HH60Gunner on 2010-02-15
anyone?

---

### Post by ironclaw on 2010-02-16
Right now, I think GRUB is looking in the /boot/ directory in the BackTrack 4 partition instead of the Ubuntu partition. You should be able to fix that in Ubuntu by reinstalling GRUB to the master boot record of your boot device. Assuming you have only one hard drive:
```
sudo grub-install /dev/sda
```

I'm not sure whether you'd have to run
```
sudo update-grub
```
but it doesn't hurt to rerun it.

I would make sure that everything in /boot/grub/menu.lst (or /boot/grub/grub.cfg if you are using GRUB 2) is correct before rebooting.

---

### Post by makingtheswitch on 2010-03-31
Thanks, ironclaw.
I had this exact same problem arise last night when I installed backtrack to a new partition.  I couldn't remember the grub-install command and syntax and was unable to connect to my wifi (no driver) with backtrack.
This should fix things up once I get home this evening.

---

### Post by kaizokuroof on 2010-03-31
The only REAL reason you'd want backtrack is for cracking WPA and WEP and stuff. You could just install aircrack-ng (I think) on ubuntu and you'd be able to do the same thing.

Backtrack is just a respun version of Ubuntu. :D

Hoping this helps you, kaizoku roof.

---

