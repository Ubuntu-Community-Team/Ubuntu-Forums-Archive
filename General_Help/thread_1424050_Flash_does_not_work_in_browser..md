---
title: "Flash does not work in browser."
date: 2010-03-07
forum: General Help
---

### Post by rreyes3000 on 2010-03-07
I have firefox installed and recently videos have not worked or has very bad mosaic picture. I am unable to hit the play button to watch videos. And when I try to watch a video in movie player it is very mosiac and unwatchable. All this started a few weeks back when I updated Ubuntu via update manager. Also, Everytime I want to print the printer is offline and need to reinstall the printer. 

Any suggestions?

thanks, Ruben

Ubuntu 9.10

---

### Post by tom4everitt on 2010-03-07
I've seen several people having trouble with different stuff after upgrading from 9.04 to 9.10, but for which the problems disappeared after a fresh installation of 9.10. So I guess that might be worth a shot. 

Otherwise you could of course try:

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 

to fix flash for example.

---

### Post by lidex on 2010-03-07
Have a look at lovinglinux's firefox optimization thread:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

