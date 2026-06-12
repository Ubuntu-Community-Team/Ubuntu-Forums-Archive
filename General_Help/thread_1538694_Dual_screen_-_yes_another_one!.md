---
title: "Dual screen - yes another one!"
date: 2010-07-25
forum: General Help
---

### Post by Jeroen De Dauw on 2010-07-25
Undoubtably the over 9000th thread about the wonderfull dual monitor suport Ubuntu has...

I have a recently installed, fully updated, Kubuntu. Worked perfectly on a single monitor. I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?p=1773624") and now get stuck at the kubuntu load screen when I boot. Weeeee.

So I want to know how to fix the load issue, and then how to get my dual monitors working. Windows fails, but ubuntu fails harder yet for dual screen, seriously >_>

I have a 64 bit system with nvidea graphics card.

---

### Post by gcbzzzz on 2010-07-25
before messing with X configs, learn how to use the standard terminals (ctrl+f1, sometimes ctrl+alt+f1)

learn where X writes log files (usually /var/log/X)

find the errors on the end of that log file (usually EEE: wrong syntax for bla) and then search that error online.

you will solve your problem very quickly. :)

---

### Post by Jeroen De Dauw on 2010-07-26
So is there a way to fix the config file from Windows (that's the only thing I have on the same machine)? I made a backup of it, but that doesn't help me if I get stuck at the load screen :(

---

### Post by P4man on 2010-07-26
boot in to recovery mode. From there try the "x fix" if that option still exists. 

If not; just go to a root shell (again from recovery mode) and delete or rename your xorg.conf. You dont really need one; and you shouldnt have to do anything special to get multimonitor working with the nvidia drivers. Just run the nvidia configuration applet. 

The instruction you followed are 6 years and 12 ubuntu versions old and simply no longer needed or applicable.

---

### Post by Jeroen De Dauw on 2010-08-03
Ok, got it fixed... I guess opening the panel and hitting apply was to obvious for me :D

---

