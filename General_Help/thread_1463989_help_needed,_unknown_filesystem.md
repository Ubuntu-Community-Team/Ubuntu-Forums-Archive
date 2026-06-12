---
title: "help needed, unknown filesystem"
date: 2010-04-27
forum: General Help
---

### Post by markuslee on 2010-04-27
ubuntu complete install failed, not i am getting the following error

                [B]Grub Rescue > Error: Unknown Filesystem

i need help
[/B]
when i turn on my computer this is what loads, f11, f12 or delete don't  grant me access to bios, what should i do

---

### Post by limey_rick on 2010-04-27
Can you start the PC with an Ubuntu Live CD in the CD/DVD reader? If so, you could boot into a Live CD version and then have a look to see what the problem is. 

GRUB should have nothing to do with your BIOS, so I don't know why you cannot access it. Is this a desktop or laptop? If its a desktop, maybe check and see how you can reset the BIOS with a CMOS jumper or removing the CMOS batter for a while.

If you boot from a Live CD, see this for more help:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Also, run fdisk -l to see what disk you have and what file types they are.

---

### Post by oldfred on 2010-04-28
From the liveCD run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

