---
title: "Need Help - Missing UI"
date: 2009-12-28
forum: General Help
---

### Post by dxtac1 on 2009-12-28
About a week ago I started having issues with Karmic freezing. I've read in this forum this may be due to a plethora of things but I'm believing it may have been Rhythmbox and or the Torrent agent being left open then the system not being able to recover from standby. Anyway that's the least of my problems right now. Yesterday I fired up the pc and the updates updates and began to install. About half way through the install the screen went black and frooze. I had been doing hard shut downs as no keyboard combinations would work. After start up I now get "dxtac@dxtac-homepc:~$". 
 
I was working with a fellow forum "Guru" and tend to agree that it *_may_* be due to my Nvidia GeForce 6100 graphics card and a kernel update not playing nicely together. We tried to go online with "wget http://tinyurl.com/y9dtms4" to update the drivers with no success. I did download the drivers to a thumb drive and through trial and error I believe we successfully downloaded the drivers to the machine successfully however I am back to square one as when I boot it asks for my username and password and brings me back to dxtac@dxtac-homepc:~$
 
I very recently switched all of my pc's over to Ubuntu in the hopes that I was leaving these goofy issues behind with MS. My netbook and notebook updated without issue, I am afraid to update my other pc for fear of this happening to that machine as well. 
 
Any and all help would be GREATLY appreciated. If I could just "Restore" back to a week ago that would be great or if anyone has any suggestions I am open. Also, if it appears the graphic card is the issue, is their a card that is recommended that works seamlessly with Ubuntu??
 
Thanks in advance,
 
Derek

---

### Post by phidia on 2009-12-28
What happens when you type > startx and press the enter key at that prompt? You may find some helpful info by typing dmesg <enter> and checking xorg logfiles in /var/log too.

---

