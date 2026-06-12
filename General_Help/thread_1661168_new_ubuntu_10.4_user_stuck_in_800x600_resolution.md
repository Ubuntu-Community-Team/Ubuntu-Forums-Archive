---
title: "new ubuntu 10.4 user stuck in 800x600 resolution"
date: 2011-01-06
forum: General Help
---

### Post by aarondem on 2011-01-06
Hello, ive been a windows user my whole life and have always known that  Linux was the better operating system by a million times, however i  finally saw the light yesterday and vm'ed ubuntu at work.  As soon as i  got home i installed a dual boot situation with half of my computer at  home now being dedicated to Ubuntu.

After a what seemed very  clean install, Ubuntu booted to the desktop and the upgrades window  popped up and informed me i had 210 upgrades to download.  I did so,  and  than rebooted the machine.  After this i went into System >  Preferences > Monitors and saw that only 2 resolutions were  available...800X600 and 640X480, and my monitor was unknown


I  think all non LCD monitors (ancient monitors) show up as unknown from  what ive been told, but i took the lack of resolutions when i know my  monitor goes much higher than 800X600 as  "looks like i need the driver  for my onboard graphics card installed"

First i did a bit of  research and saw that some people mentioned simply adding the  resolutions into your xorg.conf file located in /etc/x11/      This file  doesnt exist on my system, and when i do a search for it all i find is  an example file and a manual file, neither of which are named exactly  xorg.conf

So  i opened the package manager and downloaded the  unichrome graphics drivers and installed the package.   (My graphics  card is a VIA/S3 Unichrome Pro integrated graphics card)    After  installing i checked the package was installed successfully, and than  rebooted the machine.  Nothing changed. I still have only 2 resolutions  and 800X600 is the highest


All in all:  I have no xorg.conf  file,  i downloaded the unichrome drivers for my card via the package  manager and installed them which didnt work.  I downloaded the unichrome  drivers manually and have not installed them manually because i just  dont know how yet.  Apparently there are a few sudo commands i have to  execute on certain files in the directory , does anyone think manually  installing the same drivers that the package manager installed which had  no effect is going to change anything?

And if not, what should i  do?  I just want 1024x780 is all, is it possible to make my own  xorg.conf file and just put it in the /etc/x11/ directory?   OR Is there  a program that generates a xorg.conf file and places it in the  appropriate location?

---

### Post by sohlinux on 2011-01-06
try going to the menu - system  - admin - additional drivers it may show additional drivers for your graphics card which will support 1024

---

### Post by lrgmmc on 2011-01-06
have you looked at openChrome? it's the open driver for your videocard. here is the ubuntu doc's page for it. [https://help.ubuntu.com/community/OpenChrome#Ubuntu 10.04 LTS](https://help.ubuntu.com/community/OpenChrome#Ubuntu 10.04 LTS)

---

### Post by aarondem on 2011-01-06
Oh my, after a quick read-over on the open chrome package, which i have not gotten, looks promising!  Im excited for this i hope it works.  Going to try it first thing when i get off work, thank you SO much for the help.  Ill post weather or not it works.

---

### Post by Grenage on 2011-01-06
If you don't get the option for the resolution you need, and the openchrome driver doesn't help, I have a rough guide to xorg.conf custom resolutions [here]("http://www.grenage.com/xorg.html").

---

### Post by aarondem on 2011-01-06
Hey the openchrome drivers didnt work, BUT your guide on the xorg.conf file, i cant believe it, did.  I used the sudo apt-get xresprobe  and than sudo ddcprobe          than i made my own xorg.conf file and sudo cp xorg.conf /etc/X11/


Restart

And i now have a list of resolutions all the way up to 1400 x something  and they all work perfectly.  Thank you all so much for the help, and now i can move on with enjoying linux!

---

### Post by Grenage on 2011-01-07
I'm happy to hear that; well played. :)

---

