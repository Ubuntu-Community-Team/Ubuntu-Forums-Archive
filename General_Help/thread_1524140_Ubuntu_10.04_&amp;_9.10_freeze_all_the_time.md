---
title: "Ubuntu 10.04 &amp; 9.10 freeze all the time"
date: 2010-07-04
forum: General Help
---

### Post by vladcambridge on 2010-07-04
I have been using Ubuntu for about 2 months now, I have quite enjoyed using it and so I decided to install it on my brother's PC.
I started by trying to install 10.04-64bit, to my surprise it froze during installation. I tried installing it again and this time I was able to complete the installation, however the PC started freezing systematically usually 2-5 minutes after logging in. I decided to install 9.10-64bit, it was frustrating to discover that the same issue was still there (the systematic freezes). I also tried the 32-bit version of 10.04 but it simply didn't solve the problem.
Another thing is that when installing ubuntu from alternate CD it doesn't freeze during installation, which is not true for a regular installation image.
After reading around I discovered that booting Ubuntu in rescue mode and then choosing the failsafe option in the menu prevented any freezes from happening.
When the PC is frozen neither mouse or keyboard are responsive & the caps light DOESN'T blink.
It is certainly not a hardware problem as windows seems to work flawlessly on the machine.
Also when I do a hard restart, I sometimes need to reset the BIOS as it gets messed up.

hardware:
MB: ASUS A8N-VM
VIDEO: On-board (Nvidia 6100)
Proc: AMD 3000+
Ram: 2GB

I hope you guys can help, as I don't want my brother to give up on Ubuntu.

Any help is greatly appreciated!

---

### Post by vladcambridge on 2010-07-05
*bump*

---

### Post by oshirowanen on 2010-07-05
Stick to 8.04LTS until EOL.  By that time, 10.04 will have less bugs.  I am still using 8.04 and it works perfectly for me.

---

### Post by vladcambridge on 2010-07-05
Thanks for advice I will try 8.04 and feedback as soon as I get it installed.

---

### Post by vladcambridge on 2010-07-05
I tried 8.04-64bit and 8.04-32bit, both freeze during installation at different times.

---

### Post by ScottWish on 2010-07-05
Try new disks...

---

### Post by vladcambridge on 2010-07-05
I am installing ubuntu from a USB drive, in addition I have tried installing it from a CD which I used to install ubuntu on my laptop. Ubuntu freezes no matter which installation source I use.

---

### Post by vladcambridge on 2010-07-05
Is there any other info I could provide in order to help you understand the problem?

---

### Post by celldweller1591 on 2010-07-05
Try acpi=off option while installing in 10.04 or anyone you want. [[IMG]http://img200.imageshack.us/img200/8799/menuf61.th.png[/IMG]]("http://img200.imageshack.us/i/menuf61.png/")

Then see if it works. If it does, then install it. Logout and logback in as admin. Then open terminal and type : 
>  sudo gedit /etc/default/grub and fine the line 
>  GRUB_CMDLINE_LINUX and replace it by 
>  GRUB_CMDLINE_LINUX="acpi=off" and save it and restart the system and see if it works fine. I had same prob with karmic and lucid and fixed it using the same !!

---

### Post by vladcambridge on 2010-07-05
Thanks, it worked! I simply had to run update-grub and all the problems faded away.

---

### Post by bmdavis on 2011-01-11
That worked for me too.  Thanks!

What exactly does it do "acpi=off".  ?

---

### Post by bmdavis on 2011-01-11
Standby disabled for laptops?

---

