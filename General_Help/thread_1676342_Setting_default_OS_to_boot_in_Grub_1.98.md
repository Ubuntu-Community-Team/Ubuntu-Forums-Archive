---
title: "Setting default OS to boot in Grub 1.98"
date: 2011-01-27
forum: General Help
---

### Post by jbarntt on 2011-01-27
I Just updated my 10.04 LTS system, which dual boots Windows XP. Prior to the update the default was to boot to XP, now it is to Memtest.

I tried to edit /etc/default/ grub and make the default be 14 instead of 12, which would be XP, but Ubuntu, (using gedit), refused to accept my change.

I don't have a problem scrolling around to pick XP, or the latest Linux kernel to boot, but my wife sure does. How can I make Ubuntu/Grub default to to XP ?

TIA

jbarntt

---

### Post by jbarntt on 2011-01-27
answering my own question:

open terminal window

sudo gedit /etc/default/grub

edit default line to the appropriate number, in my case change from 12 to 14. save.

In terminal window sudo update-grub

reboot, XP is now the default boot option.

This is stupid. I knew to count from 0 instead of 1 on the grub boot menu, most people won't. Most people will have no clue re: sudo. Most people will have no clue as to the file to edit. They will also know nothing about the terminal window.

Lastly, most people would wonder why the default boot option was changed, esp. when it was changed to the memory tester ? The memory Tester ?? Who wants their system to boot to that by default ?

Ubuntu and/or grub is brain dead in this regard.

This problem occurs via the Ubuntu updater. It should be fixed.

---

### Post by Elfy on 2011-01-27
[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

Should get the information you need from there.

---

