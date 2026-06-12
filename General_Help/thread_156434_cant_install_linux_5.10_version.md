---
title: "cant install linux 5.10 version"
date: 2006-04-07
forum: General Help
---

### Post by mihrel4 on 2006-04-07
my pc Spec is 
256 ddram memory 
amd sepron processor sochet 465
14 inch monitor 
w/ built inon motherboard vedio card
why i connot install linux 5.10?
my pc promt me that  the x server failed

---

### Post by Sutekh on 2006-04-07
The X server failed?  Um, did you get through all the installation?  You know partitioning, installing GRUB, etc?

When you get this error are you left at a command line?  

It's probably your on-board video.  Can you provide some more specs on it?

Try this command to reconfigure the X Windows server
```
sudo dpkg-reconfigure xserver-xorg
```
 - use you login password when asked

 - you will get asked a long list of questions about the mouse/keyboard and monitor setup.  If you are unsure accept the default/suggested values

 - when you get to the stage about deciding on the video driver, choose 'vesa'

 - once that's finished, try ```
sudo /etc/init.d/gdm restart
```

---

