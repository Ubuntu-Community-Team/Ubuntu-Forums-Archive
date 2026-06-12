---
title: "Resolution issues"
date: 2006-03-28
forum: General Help
---

### Post by benjfield on 2006-03-28
I am using KDE, and recently installed the newest nvidia drivers, as shown in the tutorial on these forums. However, since install, the only resolutions i have been able to use are 640x480, and 320x240. Previously I was able to use resolutions that were far higher. Any help would be appreciated. Thanks

---

### Post by red_shrike on 2006-03-28
Check your monitor horiz/vert refresh settings in it's manual/online and drop back to the terminal:

ctrl+alt+f1

Log in as normal and reconfigure your x server:

Code:

$sudo bash Password: <your pass> 
# /etc/init.d/kdm stop 
# cp /etc/X11/Xorg.conf /etc/X11/Xorg.conf.backup 
# dpkg-reconfigure xserver-xorg


Choose the advanced or medium setup option, armed with your monitors refresh values, entering when prompted (advanced).

Finally, when you are finished, start up kdm again:

Code:

#/etc/init.d/kdm start


This is the exact same problem many other users have; these instructions are by Ali, but they are good so I have copied them (long live OpenSource)! Thnx Ali. Tell us how it went along. 

red_shrike

PS
Alternatively you can look in /etc/X11/xorg.conf and change some options to your liking (maybe try lower color depth).

---

