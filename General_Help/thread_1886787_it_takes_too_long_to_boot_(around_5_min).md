---
title: "it takes too long to boot (around 5 min)"
date: 2011-11-25
forum: General Help
---

### Post by jjmcclure on 2011-11-25
Hello, I'm new in the forum and my problem seems to be quite common and I have read a lot possible solutions and tried so many things but so far the problem is still there.

My problem is that when I choose in the grub the option ubuntu to start up, the screen turns purple and it takes about 2 and a half minutes to show the login screen, then after that it takes about 2 minutes to be completely operative.

I use a desktop and I have Ubuntu 11.10 but it also happened with older versions (10.04 10.10 and 11.04).
I have tried to start from the console but when I add "text" after "quiet splash" in the grub, the purple screen never disapears and I can't even log in.
I have read that disabling USB Legacy Support solves the problem but I don't have that in my BIOS and I want to use a USB Keyboard and mouse.

I don't know what to do.

Can anyone help???

Thanks.

---

### Post by BC59 on 2011-11-25
You didn't specify the data of your computer.

If you use 500Mb of RAM for example 2min is acceptable time.

---

### Post by jjmcclure on 2011-11-25
My computer has 24 Gb of RAM

---

### Post by hal8000 on 2011-11-25
When you add text at the grub prompt remove the words quiet and splash, you should then see boot messages on the screen as Ubuntu loads.

Watch carefully and post the lines that take a long time to respond. 24G of RAM will only be used if you are running the 64bit version of Ubuntu.

Another way is to use synaptic and install bootchart to produce a boot graph.

---

### Post by bluexrider on 2011-11-25
Whooo! 

Thats strange. I have a AMD sempron 2800xp 2Gb ram and 3 HDDs. I'm booted in 48s after grub. Log-on in 14s.

Must be running some heavy duty processes. Get the bootchart 

bootchart allows you to audit the boot sequence of your computer and
generate a pretty chart of the processes run, including how long they
took and how much CPU and I/O they used.

The auditing is performed by a tool that runs in your initramfs, or
early in your boot sequence, and records system statistics as your
computer boots.

Tarballs of this data are left in /var/log/bootchart; from these either
PNG or SVG will be generated if pybootchartgui is installed.

---

### Post by jjmcclure on 2011-11-28
Thanks for the replies guys.
I did the bootchart and the results are in the tar file attached.

What do you think??

---

