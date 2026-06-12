---
title: "printing to parallel PERMISSION DENIED"
date: 2012-04-17
forum: General Help
---

### Post by littleknowledge on 2012-04-17
Hello everyone, thank you for reading this thread.  

I am running ubuntu server 11.10, I am trying to send raw data to a printer via parallel port. I had assumed that:

cat print.txt > /dev/parport0
or
cat print.txt > /dev/lp0

would work, but everytime i run the command i get 
-bash: /dev/lp0: Permission denied

lsmod shows: parport  40930  3 ppdev,parport_pc,lp

permissions show: 
crw-rw---- 1 root lp 99, 0 2012-04-17 16:00 /dev/parport0
crw-rw---- 1 root lp 6, 0 2012-04-17 16:00 /dev/lp0

I tried running as 'sudo' but same thing.... I didnt want to install CUPS as i dont need any print driver, any ideas why it wont let me print?

---

