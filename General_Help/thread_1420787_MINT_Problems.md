---
title: "MINT Problems"
date: 2010-03-03
forum: General Help
---

### Post by pgoffa01 on 2010-03-03
Hi all, 
Emachines W2040 Athlon, triple boot. Open SUSE 11, WinXP SP3 and Mint 8 (gnome). Have been using current config for months with no issues other than the regular Microsoft headache. Now today, I was in MINT and restarted to reload the GRUB menu. This time, when I restarted, I went to the Mint directory because I forgot something and it popped up an all black log in screen and in the upper right hand corner, a box would appear saying something about Gnome configuration error. I restarted again, this time it wouldnt boot to log in screen. It shows the MINT logo and freezes. I restarted again and this time went to recovery mode. For ten minutes, I watched it tell me that there was an error -71 unable to enumerate USB and it still wont load. Is there anything I can do? I really don't want to have to reinstall.

---

### Post by tgalati4 on 2010-03-03
A cluster of strange problems point to a possible hardware problem.  Boot in rescue mode or with Live CD and look at the files in /var/log:

cat messages
cat messages.0
cat syslog
cat syslog.0

Look for errors or unusual behavior.

Could be RAM, powersupply, failing motherboard, hard disk.  Hopefully your log files will capture something.

---

