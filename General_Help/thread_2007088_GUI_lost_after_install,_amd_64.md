---
title: "GUI lost after install, amd 64"
date: 2012-06-20
forum: General Help
---

### Post by Rsjc741 on 2012-06-20
Just a quick question. Someone with a lot of experience might be able to help me out.

I'm running 12.04, and it seems to have a ton of bugs when it comes to the 86_64 platform.

Anyways, I've updated Ubuntu to the absolute latest stable release, but there seems to be an issue with my nvidia gtx 560 ti.

When booting, theres no GUI. Any attempts to use startx is met with SN error refering to a wrong configuration.

The CD worked fine.

How can I get my GUI back?
It connects to the internet btw.

Gnome is preferable.

---

### Post by NotSoRandomUsername on 2012-06-20
Goto /etc/X11 and see if there are any xorg.conf backups try restoring those. And post a little more info about the error you get and what you did before this occured.Don't forget people do this for free you can just demand someone with allot of experience.

---

### Post by Rebelli0us on 2012-06-20
I had a similar problem, it seems that newer Nvidia hardware is not well supported in Linux. [But I got my NVIDIA GTX 550 Ti working under 10.10]("http://ubuntuforums.org/showthread.php?t=2002356")

---

### Post by Rsjc741 on 2012-06-20
Sorry, I'm on my phone, so its incredibly painful to type out long, drawn out, discussions. =/

Here's my specs:

AMD FX-8150 CPU
ASUS M5A97 Mobo
16GB RAM
NVIDIA GTX 560 To (PNY XLR8 series)
128GB SSD.

There is no starting error. Ubuntu just boots into a terminal.
When I start xserver however, it tells me that "Screens found, but but none have a usable configuration".
Then it ends in Error 1

I've tried replacing the regular config file with the fail safe, but no dice.

There is no backup, as this started right after installation.


Oh, and I have UEFI BIOS, and running Ubuntu as an EFI drive.

And Ubuntu hates my computer if I try anything under 12.
My wireless card does not play nice and usually makes the whole system unstable. So its nice that its finally supported in 12.04.

---

### Post by gordintoronto on 2012-06-20
Have you tried nomodeset?

If that works, try:
Add in Software Sources: ppa:ubuntu-x-swat/x-updates
Now you can install a later version of the video driver, which works for most systems.

---

### Post by jmfal on 2012-06-20
Exactly  Gordintoronto,  Had same problems from start with 12.04

installed swat-x  ppa

No problems  to date...

---

