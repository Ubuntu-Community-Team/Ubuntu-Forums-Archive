---
title: "Restricted driver problem"
date: 2009-11-01
forum: General Help
---

### Post by prodigalson666 on 2009-11-01
Installed 9.10 with no problems, updated no problems, activated restricted ati drivers, restarted 1st I get umsupported mode warning on my monitor, then I restarted again now at the laod screen it runs a test, then it tells me mount of file system failed and that a maintenance shell has started!? Ani ideas? Thanks.

---

### Post by lavinog on 2009-11-01
What video card do you have?

---

### Post by retrow on 2009-11-01
It had happened to me during Karmic Alpha era. When you are dropped to shell mode, you might want to run the fsck for all of your ext3/ext4 partitions. Then, [color=blue]sudo shutdown -r 0[/color] and see if it restarts correctly.

---

### Post by prodigalson666 on 2009-11-01
Im using ATI 4350 card. I have tried several distros and have the same problem after install, fedora, mandriva etc. Is it my video card? It seems that getting distros and video cards to work together is getting worse from my experience recently. I havent used linux in a year but previous to this I had nothing but flawless installs and good experiences from many distros out there.
Should I use an older distro or older video card or perhaps an nvideo card? I uninstalled ubuntu in countless frustration so Ill have to decide if I want to bother with the 2nd posters suggestion. Thnkas for the help guys and gals any further help or insight would be appreciated.

---

### Post by lavinog on 2009-11-01
can you post any logs or take a picture of the last couple of dmesg lines?

---

