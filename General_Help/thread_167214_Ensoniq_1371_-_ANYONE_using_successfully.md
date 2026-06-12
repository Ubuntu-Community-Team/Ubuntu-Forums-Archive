---
title: "Ensoniq 1371 - ANYONE using successfully?"
date: 2006-04-28
forum: General Help
---

### Post by daboochmeister on 2006-04-28
Hi, all, I have an Ensoniq 1371 card, and after having tried everything I can find from every thread and every website everywherre, I still have no sound.  I get static and a very very faint amount of sound if I unmute the "IEC958 1" in alsamixer, but that's the only thing even moderately approaching success that I've achieved.

Note that by following instructions from other threads, I've confirmed my kernel has module support,  modprobe -l returns:

[INDENT]modprobe -l | grep 1371
/lib/modules/2.6.12-10-386/kernel/sound/oss/es1371.ko
/lib/modules/2.6.12-10-386/kernel/sound/pci/snd-ens1371.ko
[/INDENT]

etc. etc.

So ... is there **anyone** who has the card successfully configured?  At this point, I'd like to simply copy your ~/.asoundrc, /etc/modutils/alsa-base, etc. etc.

Note I'm using Kubuntu 5.10, uname -r returns 2.6.12-10-386.

Tia for any help!

---

### Post by multios on 2006-04-28
I have the same chip :) 
Use the OSS driver (es1371). 
"modprobe -r snd_ens1371"
"modprobe es1371"   Do these commands as root (or sudo).
In KDE control center, under sound/sound system, click hardware tab, and in the audio device setting, choose oss. Sometimes, the autodetect will work, but seems best of just using oss. 
HTH :) 
Under kmix, mute the IEC stuff.  It works like a champ for me with these settings.

---

### Post by daboochmeister on 2006-05-01
Thx, multios.  A couple of quick attempts didn't work for me ... I'm assuming I have to e.g. blacklist the ens1371 to keep it from being reasserted by hal at boot (??  yes/no?  :-k ); and i think my customized modprobe.d/alsa-base, asound.conf, and .asoundrc files may be hurting me.  

Is there any chance you could post your various config files?  That may be the key that unlocks this whole thing for me.

Thanks for giving a powerup to my flagging hope on this!  :D

---

### Post by multios on 2006-05-01
My apologies :( 
It does require the oss module and that is what worked for me on HH. 
2 days ago (not longer after posting my first reply), I downloaded BB to try it. 
For some reason, I can't get alsa to stop loading. I have even named every alsa file/directory to ALSA or a different name altogether, and renamed the snd-ens1371.ko file also. The system still boots and when I do a lsmod |grep 1371, it still shows snd_ens1371!  
I have also added es1371 to my /etc/modules file (I think), but have to see if that will work now as soon as I reboot.
I do not know why the chip worked so easily with HH and not BB unless it was a change in the alsa program. 
Do a search on "prevent alsa from starting" and you will find my question there also. 
I run PCLinuxOS, Slackware, Kanotix, and several other distros and so far only OSS works with that chip on each distros. 
On PCLinuxOS, you can choose which module to use and that's it. Sweet :)

---

### Post by multios on 2006-05-01
daboochmeister, do a modinfo and see if you have the snd-care-audiopci module. If you do, try loading it. That is some info I just found. 
I doubt you do, since I don't have it (at least on my BB). 
I am going to check my other systems and see if that module is on them.
HTH.

---

### Post by multios on 2006-05-02
I finally got it working with BB, but it was a pain and I used OSS. 
I am listening to an audio cd right now. 
I got messed up between files for 2.16.9 and 2.16.10. 
Once my head clears and I can calm down a bit, I will write down what I did, but it may not be all accurate because of mistakes between the two kernels. Besides that, I started with a fresh install of BB to see if it would work that way. Blew it with the upgrading :( 
So far, I have only got the Ensoniq 1371 to work correctly with OSS. It works somewhat with alsa, but no settings would be saved between reboots. 
More later here or/and on the gnome forum.

---

### Post by multios on 2006-05-03
I am using alsa/snd-ens1371 with Ubuntu and kernel 2.6.12-10-386! !

I did another fresh install of BB and did upgrades before starting anything. 

Before rebooting with the new kernel I added "snd_ens1371" to /etc/modules. I then rebooted. 
Before logging in with gdm, I went back to a console login (ctl-alt-f1), logged in and then did the following commands: 

sudo modprobe -r snd_ens1371 
sudo modprobe snd_ens1371 

I then logged in with gdm and I have sound! I am again listening to a cd while writing this. 
btw- I never touched alsaconf, alsamixer, or alsactl. 

Also, I haven't yet run easyubuntu or automatix. I will try one of those next (probably automatix), to install everything else.

HTH
multios

---

### Post by daboochmeister on 2006-05-07
I'm glad it got working for you ... I ended up on SUSE (for a different reason -- I was having a grub problem where everytime I tried to have Kubuntu and SUSE together, Grub would start throwing errors), and deleted my Kubuntu partition.  On SUSE, this card worked fine after running alsaconf.

That was actually one of my confusions w/ Kubuntu -- I could never find alsaconf to run.  Is it not included in the alsa-tools on debian derivatives for some reason?

Anyway, when I get a chance, I'll try to come back here and post my settings files from SUSE, for future reference.  They won't be directly usable as is, because of the differences btwn the distros, but may have some value for people.

Thx!

---

