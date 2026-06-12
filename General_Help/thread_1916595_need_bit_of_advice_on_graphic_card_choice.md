---
title: "need bit of advice on graphic card choice"
date: 2012-01-28
forum: General Help
---

### Post by rvboutin on 2012-01-28
Hi,
I am building a new PC at home and I want to run Windows 7 64bit and Ubuntu 11.10 64bit in dual boot.
I have at work 2 PC, one with an ATI card the other with a nvidia card, with both at some point I had to solve display problem, whether when installing catalyst driver or with the driver utility from nvidia (impossible to get dual display, no display at all, etc..). So really I am none wiser than before about picking the right brand of card... I have been perfectly happy with AMD/ATI card on my Windows systems before, and their price/performance is good for me. I do occasional gaming on Windows but not much.
To work (@ home), I need a reasonably powerful card to handle large 3D image file and some videos, and this under Windows and Ubuntu.
I was going for an Asus Radeon HD 5770 or Radeon HD6570 but I saw few problems reported on this forum and other... and especially that "...RadeonHD 6xx0 chips will need kernel 2.6.38 for open-source mode-setting, xf86-video-ati/radeon 6.14.0 for 2D acceleration (EXA/Xv), and Mesa 7.11 for 3D acceleration." (see here: [http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware"))
As Ubuntu 11.10 is now running the kernel 3.0, would this card work? I guess I'd need the AMD/ATI catalyst proprietary driver? Which version is best to use? AMD now provide the version 12.1 of the catalyst driver, any feedback about it?
Thank you in advance for your help.
Rv

---

### Post by jboniello on 2012-01-28
I recently installed a msi AMD radeon 6670 card in my desktop.  11.10 in 3d mode (default desktop environment) has not worked for me, it freezes after it loads to the desktop background.  I would not recommend one of these simply due to that reason.  I have posted on here and I have not gotten an answer as to how to try to fix it.  I have searched for answers, no luck.  Again, I would stay away from something like that unless you know how to get it to work.  For 2d mode it works fine.  I did install the fglrx driver from ati.  Good luck!  BTW, the card works wonderfully under windows.

---

### Post by sudodus on 2012-01-28
I have an nvidia Geforce GTX 430 card, and I can use hardware acceleration in Ubuntu (when I run the *built-in proprietary driver* and mplayer with vdpau). The graphics is still not quite as smooth as in Win XP, but I am fairly satisfied with it. I have still not managed to install the newest proprietary driver downloaded from nvidia's web page (it is too difficult for me).

---

### Post by Cheesemill on 2012-01-28
I've always had a lot more luck with Nvidia cards than ATI.

---

### Post by Bobhuber on 2012-01-28
> **sudodus said:**
> I have an nvidia Geforce GTX 430 card, and I can use hardware acceleration in Ubuntu (when I run the *built-in proprietary driver* and mplayer with vdpau). The graphics is still not quite as smooth as in Win XP, but I am fairly satisfied with it. I have still not managed to install the newest proprietary driver downloaded from nvidia's web page (it is too difficult for me).
Don't - The 290.10 driver breaks Ubuntu  system monitor with the GTX 430 card. Stick with 285.05.09 untill they come up with a fix.

---

### Post by Bobhuber on 2012-01-28
+ 1 for Nvidia

---

### Post by sudodus on 2012-01-28
> **Bobhuber said:**
> Don't - The 290.10 driver breaks Ubuntu  system monitor with the GTX 430 card. Stick with 285.05.09 untill they come up with a fix.
Thanks for warning me :-)

---

### Post by rvboutin on 2012-01-29
@jboniello
I found several advice on various forums including this one. One common thing that seems need to be done is to initialise the ati configuration after installation and **before **reboot with this command:```
sudo aticonfig --initial
```
So here are several links that I hope will help you:
[LIST]
[http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric]("http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric")[/LIST]
[LIST]
[*][http://askubuntu.com/questions/67065/system-doesnt-boot-after-amd-11-9-driver-install/67169#67169]("http://askubuntu.com/questions/67065/system-doesnt-boot-after-amd-11-9-driver-install/67169#67169")
[/LIST]
[LIST]
[*]post#5 here [http://ubuntuforums.org/showthread.php?p=11343771]("http://ubuntuforums.org/showthread.php?p=11343771")
[/LIST]
[LIST]
[*]and general information here: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29")
[/LIST]
Hope this help :)
Rv

NB: I used the advices above to remove/reset the proprietary driver on 1 of my work PC and that solved the problem (I do not remember the ATI card I have on that PC right now, I think a Radeon HD 4xx0 series).

---

