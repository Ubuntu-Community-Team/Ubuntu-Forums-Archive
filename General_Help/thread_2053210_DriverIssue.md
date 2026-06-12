---
title: "DriverIssue"
date: 2012-09-04
forum: General Help
---

### Post by Cubone2 on 2012-09-04
New to Linux. I have downloaded drivers from the manufacturers website, but haven't got a clue how to install them. I tried the readme.txt file. It was beyond  me interpreting the readme.txt. I would like to install ASUS drivers onto my machine.

---

### Post by sienile on 2012-09-04
You need to be more specific. What ASUS drivers? (They make tons of stuff.)

What kind of file did you download? (.tar.gz, .deb, something else?) If you downloaded a .exe it will not work.

---

### Post by Cubone2 on 2012-09-04
"Linux_PCE_N15_1008" is the file I downloaded from ASUS. Ends with zip. Its for my wireless Card. I want to know how to make it in the terminal. Was confounded reading the text. Build-Essentials is not in the software center before you ask? Thanks for replying.

---

### Post by Cubone2 on 2012-09-04
"Linux_PCE_N15_1008"  is the file I downloaded from ASUS. Ends with zip. Its for my wireless  Card. I want to know how to make it in the terminal. Was confounded  reading the text. Build-Essentials is not in the software center before  you ask? Thanks for replying.

---

### Post by sienile on 2012-09-05
You gave much more detail in the private message you sent to me, so I'm including it here.
[QUOTE=Cubone2]Sorry for the not so complete thread. I am new to LINUX. I can't get my wireless "ASUS PCE-N15 PCI-E 1x 300Mbps Wireless-N Network Adapter" to connect to my "Trend-net TEW-432BRP" router. I thought maybe the wireless driver needed installing. I downloaded it from ASUS. It is a zip file labeled " Linux_PCE_N15_1008". Thanks in advance.[/QUOTE]

After reading through the readme, it seems to be a straight-forward "make" install with no configure script. The instructions are laid out in heading II, but I'll post them here too.
```
sudo su
make
make install
reboot
```
Of course you need to extract the zip and cd to the directory you extracted it to first.

P.S.: Welcome to Linux. ):P I'm a new user myself. Only been using it for 2 months. Once you get used to it, you'll never use Windows again.

---

