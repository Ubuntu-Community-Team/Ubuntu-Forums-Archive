---
title: "Need Help with Sound Issue -- PLEASE"
date: 2011-09-19
forum: General Help
---

### Post by Cpierce on 2011-09-19
I need help. I am working on a friend's computer installing 10.04. I am trying to convert everyone I know to Ubuntu. His computer is a Samsung Q430 with an i5 2.67ghz processor, nVidia GeForce 310M, 4GB RAM. I installed 10.04 and installed a ton of software. Sound worked perfectly when I was done. When installing software, I have the computer login automatically due to all the reboots, before he picked up the computer, I changed login to require a password. I went to show him how cool his new computer was and we had no sound on any application. I changed login back but still no sound. 

System Profiler shows the card to be:
nVidia Corp High Definition Audio controller(rev a1)

Sysinfo shows two:
HDA Intel-HDA Intel
HDA Intel-HDA NVidia

aplay -l shows Intel(HDA Intel) ALC269

lspci -v shows Intel Corp 5 series/3400 with HDA Intel and driver snd-hda-intel

Alsamixer shows nothing is muted and all levels are set high.

I re-installed nVidia current(195) with synaptic

I re-installed pulseaudio with synaptic

I can see the microphone moving when I talk in sound preferences

This is a duel boot setup and sound works fine in Win7 so I know the sound card is working. 

I know it is just something small because it worked perfectly before. But I am stuck. 

Can someone help me ?

---

### Post by Cpierce on 2011-09-19
I should also add that I noticed there was no sound when I tried to use Skype. When I first installed Skype and opened it, sound, test call and webcam worked fine. However, I forgot to not let skype adjust mixer levels. The second time I opened Skype a few days later, is when I got no sound anywhere on the computer.

---

### Post by Cpierce on 2011-09-20
bump please

---

### Post by Porcini M. on 2011-09-20
Try going into setting where you manage users & groups. For his user, navigate to "advanced settings" and grant him access to audio - that might work (at least it does in Xubuntu)...

---

### Post by Cpierce on 2011-09-21
I will sure try that and report back!

---

### Post by Cpierce on 2011-10-31
Solved it. It was songbird that was hung up. Killall songbird and reboot and sound is back. Weird

---

