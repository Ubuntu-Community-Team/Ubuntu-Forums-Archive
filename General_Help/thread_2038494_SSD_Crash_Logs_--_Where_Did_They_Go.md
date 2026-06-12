---
title: "SSD Crash Logs -- Where Did They Go?"
date: 2012-08-06
forum: General Help
---

### Post by angryhomer17 on 2012-08-06
My SSD is dying. It's getting a lot of I/O errors. I can see the failure through dmesg. I'm trying to copy/save these logs but by the time the SSD starts crashing the system freezes. Sometimes I can get into a virtual terminal, but can't login because the SSD is crashing.

After I reboot I cannot find the logs showing the I/O errors. I've looked at dmesg and the tar dmesg, kern, and syslog logs. None of them have any of the I/O errors that show up in the virtual terminal or dmesg in a terminal.

Where did they go? Am I not looking hard enough or in the wrong place? Thanks.

---

### Post by angryhomer17 on 2012-08-06
Instead of trying to get the logs while booted to the ssd I thought it'd be easier to get them while booted off a hard disk. I was right. 

Copied some files over to the ssd and watched it fail. Errors were in /var/logs/syslog and dmesg.

---

