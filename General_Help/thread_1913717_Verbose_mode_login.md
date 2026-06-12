---
title: "Verbose mode login"
date: 2012-01-23
forum: General Help
---

### Post by thomasmanalil on 2012-01-23
Hi,
   I am using Ubuntu 11.10 and my login is taking lots of time, specially to load desktop after login. So i would like to enable verbose mode log in where i can see the processes being started and find a fix for slow login. 
Please help

---

### Post by thomasmanalil on 2012-01-23
Hi,
I am using Ubuntu 11.10 and my login is taking lots of time, specially to load desktop after login. So i would like to enable verbose mode log in where i can see the processes being started and find a fix for slow login. 
Please help

---

### Post by plucky on 2012-01-23
> **thomasmanalil said:**
> Hi,
I am using Ubuntu 11.10 and my login is taking lots of time, specially to load desktop after login. So i would like to enable verbose mode log in where i can see the processes being started and find a fix for slow login. 
Please help

Edit the file /etc/default/grub and remove "quiet splash" from the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` so it looks like ```
GRUB_CMDLINE_LINUX_DEFAULT=""
``` then run ```
sudo update-grub
``` and it should be in verbose mode.


Good luck

---

### Post by oldos2er on 2012-01-23
Threads merged. Please don't open more than one thread per issue.

---

