---
title: "Running Programs from Windows"
date: 2010-07-03
forum: General Help
---

### Post by CHAORAIN on 2010-07-03
I have a dual boot system, Windows 7 and a WUBI installed Ubuntu 10.04, both are 64 bit. Can I use Wine to run a program installed on the Windows partition? If so is there anything special I need to do? My Ubuntu partition is really small and I:d like to keep it that way.

---

### Post by Serpher on 2010-07-03
Yes but only if the program works in WINE. Most modern programs don't. WINE is technically still in beta.

---

### Post by synapsys on 2010-07-03
> **Serpher said:**
> Yes but only if the program works in WINE. Most modern programs don't. WINE is technically still in beta.

Agreed. You will probably spend more time trying to get things to work in wine than it takes to reboot into windows. Wine is great, but for windows programs, windows is best.

---

### Post by artemyv on 2010-07-03
to run a program installed in one windows under another (wine is another instance of windows) could be a headache by itself... win-prog could require some reg-entries, specia files etc - that are put in place by installation and wine will have no idea about them till you actually install the program...

To use the trick of installing the program above itself which is sometimes used with dual-boot windows I would highly NOT recommend to use with wine...

If you still want to run your windows progrs in ubuntu - take a look at converting your windows install into virtual machine and run it inside virtual-box

---

