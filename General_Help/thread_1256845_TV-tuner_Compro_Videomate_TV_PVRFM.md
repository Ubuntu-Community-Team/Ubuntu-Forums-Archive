---
title: "TV-tuner Compro Videomate TV PVR/FM"
date: 2009-09-03
forum: General Help
---

### Post by krishna.988 on 2009-09-03
**TV-tuner Compro Videomate TV PVR/FM** 
I can not listen to radio on TV-tuner Compro Videomate TV PVR/FM. I'm using Ubuntu 9.04 and have instaleed gnomeradio.

I have followed these instructions: 
1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file:

alias char-major-81 videodev
alias char-major-81-0 saa7134
[FONT=Courier New]options saa7134 card=40 tuner=41 alsa=1[/FONT] 
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa


3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134

and these instructions

[root@mythmaster ~]# cat /etc/modprobe.conf
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=41 alsa=1
alias snd-card-1 saa7134-alsa
options snd-card-1 index=1
options saa7134-alsa index=1
remove saa7134-alsa { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove saa7134-alsa


Can anyone please help me out in listening to radio using gnomeradio and TV using TVtime.? (I have installed TV time and gnomeradio).
I don't have any issues with the TV tuner card as it works good on Windows vista. and also m a newbe to linux world?

Note: After running the above commands my realplayer use to quit whenever i tried to play an mp3 or any audio file but after changing the device to OSS on the Hardware tab in realplayer preferences ..it started working..

---

### Post by krishna.988 on 2009-09-04
I solved the issue with these settings card=40 tuner=69 option..Now I'm able to listen to radio with gnome radio.. though kradio throwed some alsa related error messages in gnome..but gnomeradio worked beautifully sound clarity is also good..

---

### Post by Shabba on 2009-09-04
Krishna I'm glad you sorted things by yourself. Shame nobody could help you :(

I have the same radio problem as you. TV, no problem but never managed to get the FM radio sorted. Can you please copy and post your modprobe.d file so that I can dissect it with hope :)

Thanks in advance

Shabba

---

### Post by krishna.988 on 2009-09-05
Shabba,

[FONT=Verdana]You need to create saa1734 file with these contents in the /etc/modeprobe.d folder
[FONT=Courier New]
alias char-major-81 videodev
alias char-major-81-1 saa7134
options saa7134 card=40 tuner=69 alsa=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

[FONT=Verdana]Do tell me with this option r u able to watch TV with TVTime..  

Thanks..
[/FONT][/FONT][/FONT]

---

### Post by Shabba on 2009-09-05
Perfect mate :)

Had to play around a little but everything is working as it should. I owe you a beer or 2 ;)

---

### Post by proggy on 2010-05-04
I never got that card to work In Ubuntu , this is how i`m plugged in from my setop box by coax cable to my tv tuner card .
In windows i have no problem using the drivers provided by compro.
It would be really cool if i got that card working in Ubuntu

---

