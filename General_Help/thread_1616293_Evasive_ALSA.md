---
title: "Evasive ALSA"
date: 2010-11-08
forum: General Help
---

### Post by vikrang on 2010-11-08
This problem is not with Ubuntu or its varaiants and is faced by me in distros where I try to build from core packages (Arch/Sabayon/Zenwalk/Salix) ...In all of the Distros my sound card is detected but I cant get the sound up
 
As many of you would have guessed by now - Yes, I have snd-hda-intel sound driver!! I know it has got to do with the model=stuff (3stack/5stack/ref/auto/dell-m42 etc) ..
 
All the blogs and tutorials incl ubuntu forums talk abt the following (pl correct If I am going wrong somewhere)
 
1. rmmod snd-hda-intel (remove old driver)
2.modprobe snd-hda-intel model=(whatever)
3.Add "options snd-hda-intel model=(whatever)" to /etc/modprobe.d/alsa.conf (This is an empty dir and I create a file named alsa.conf")
4.Reboot
 
I have tried all permutations of the models (pl dont give link of the AlSA project!! I know there are different models for different cards)
 
Is this a kernel issue ? ...Sabayon and others use 2.6.35 (Bleeding edge!! It is bleeding me!!)
 
When progressive distros like Ubuntu, Mint, SUSE, etc are able to arrest this issue, why is it not for the Build and work distros?!
 
Ideally DELL VOSTRO 1500 C2D is a decent (if not the best) which makes use of standard components (not roadside chinese cheapies!) ...Why are these distros failing time and again for so many years or upgrades?? 
 
Same is the case with Broadcom Wireless - Agreed it is a proprietary driver which doesnt reveal the code..so we have some additional work like download b43-fwcutter , firmware and upping the network ..
 
But these seem to be perennial ..,,,

---

### Post by vikrang on 2010-11-08
Just a thought  wave ...Can I install OSS4 or Pulse audio and dispense with ALSA? Maybe I will be able to play audio using these modules...Any suggestions?

---

### Post by mastablasta on 2010-11-08
i too have problem with this driver. however if i only upgrade ALSA to latest version everything works well.
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
I am not sure which ALSA is in the kernels of systems you mentioned though... so it might not solve your problem. but it did solve mine, sort of. as there is still some errors reporting and i think i can only use analog stereo duplex. i can use digital sound, however in that case the mic stops working.

---

### Post by vikrang on 2010-11-09
Thanks ...
 
Actually I am not getting sound in Sabayon..
 
But I thought issue is the same and someone may be able to help me out
 
I use Kernel 2.6.35 ..ALSA driver is latest 1.0.23 ..
 
I had some slight success today ... I did the foll as mentioned in a forum 
 
1. lsof /dev/snd/* 
2. Kill all sound related processes
3. rmmod snd-hda-intel ( In some forums they have mentioned "underscore", in others " hyphen"..Dont know which is correct...When I tried underscore I got an error that module does not exist)
4.modprobe snd-hda-intel model=5stack (I have sigmatel 9205 )
5.alsamixer -c 0 (upped the sound for Master and PCM and unmuted)
6.speaker-test -c 2

Sound was heard
 
However when I opened exaile and tried to play an MP3 , I could not hear any sound...It is not a permission issue.
 
I am trying this method , but even the test is not working- could be due to upgrade I did in Sabayon....
 
 
However I need to mention that Peppermint (ubuntu 10.04 fork I think- latest); Mepis 8.5 , PC linux OS detects and plays all sound flawlessly...Out of the box!

---

