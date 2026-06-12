---
title: "Microphone or Speakers dont work (Please look)"
date: 2009-10-28
forum: General Help
---

### Post by splosh5 on 2009-10-28
hey

i have just installed ubuntu. now on xp i would have to install my sound drivers. i am useing realtek sound card but i can hear sound from my music on my pc but when i go online e.g youtube i can watch the vid but i cant hear anything. also when i try and use GTK desktop recorder it will record the screen fine but my audio from my mic wont work either. i also have try audacity and my mic does not get picked up from that. when i go to the vol, control panel it says i have like 12 differnt sound choises. now i dont realy know alot about ubuntu due to i only installed it yesterday... sooo please i realy need your help.

---

### Post by P4man on 2009-10-28
Do I understand right that you can play sound in ubuntu (say MP3s) but only in flash you have no sound? If so, perhaps this helps. Open a terminal from applications > accessoiries and run these 2 commands to remove and reinstall flash (close firefox before doing so):.

```
sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree
sudo apt-get install flashplugin-installer flashplugin-nonfree
```

As for the microphone, not to insult your intelligence but make sure its connected to the correct plug on your soundcard. If it is, then right click the volume control, go to properties, enable all sliders and experiment with the settings. Try toggling mic boost, select the different mic inputs you likely see...

---

### Post by splosh5 on 2009-10-28
> **P4man said:**
> Do I understand right that you can play sound in ubuntu (say MP3s) but only in flash you have no sound? If so, perhaps this helps. Open a terminal from applications > accessoiries and run these 2 commands to remove and reinstall flash (close firefox before doing so):.

```
sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree
sudo apt-get install flashplugin-installer flashplugin-nonfree
```As for the microphone, not to insult your intelligence but make sure its connected to the correct plug on your soundcard. If it is, then right click the volume control, go to properties, enable all sliders and experiment with the settings. Try toggling mic boost, select the different mic inputs you likely see...

Ok i follow what u said and ive played with the mic sockets and the settings but im not sure what volume control i use because i have loads. ill and a screen shot of them please look. and im not sure what setting i use for my speakers and my mic.

---

### Post by P4man on 2009-10-28
The mixer you want to select there is the one that starts with playback (since the default mixer is your volume control),and you want a pulse audio mixer. But it looks like you have 2 soundcards in there (as well as an audio enabled webcam? Builtin mic?). Since I dont know which of both you have your speakers connected to, try both playback pulseaudio mixers.

---

### Post by splosh5 on 2009-10-28
Yes i do have my webcam plugged in atm ill unplug it.

---

### Post by splosh5 on 2009-10-28
I have just unplugged my webcam, but im relay not sure witch one i choose for it to work because there are a lot of different choices.   i would like to say though that i did install Plusaudio.
 
Please help.

---

### Post by P4man on 2009-10-28
I never said you had to unplug it. Im just pointing out you have 2 playback devices for pulseaudio, one intel hda, and one C-media. Do you have a soundcard in that machine as well as onboard sound?

---

### Post by splosh5 on 2009-10-28
no i dont have a onboad sound card because i built this pc :P i only have one sound card in it.

---

### Post by splosh5 on 2009-10-28
well, along time ago i bought a emachines pc, but then i reformatted the HDD. and i was unable to use my sound, so when i built this pc, i took that sound card out of the never used emachines pc and then put it in my new built pc. and the sound card never came with any drivers. but when i was using xp i would put my MB drivers in my drive and then install them. but the realtek sound card drivers came on the cd. so i dont think that my sound card is a realtek sound card. and im not sure what drivers my sound card needs. because all i want to be able to do is listen to music and talk with my mic.

---

### Post by P4man on 2009-10-28
then its probably the intel-hda mixer, but dont make me guess so much. If you want help, pls answer the above questions, like wether the problem is only in flash or also when playing music like in rhytmbox. What happens when you press the test sound in preferences > sound and trying the various pulse mixers (probably intel hda)

---

### Post by P4man on 2009-10-28
> **splosh5 said:**
> well, along time ago i bought a emachines pc, but then i reformatted the HDD. and i was unable to use my sound, so when i built this pc, i took that sound card out of the never used emachines pc and then put it in my new built pc. and the sound card never came with any drivers. but when i was using xp i would put my MB drivers in my drive and then install them. but the realtek sound card drivers came on the cd. so i dont think that my sound card is a realtek sound card. and im not sure what drivers my sound card needs. because all i want to be able to do is listen to music and talk with my mic.

Its next to impossible to buy a motherboard without onboard sound these days. If you plugged in a PCI sound card, then you now have 2 Im quite sure. Check the back of your pc, you will have sound jacks near the USB ports. Do you know what motherboard it is ?

---

### Post by splosh5 on 2009-10-28
well ive found out that if i set them all to: OSS Open Sound System and when i click test it works fine but i dont know how ill find out what one it is for my mic?

---

### Post by splosh5 on 2009-10-28
OW OK yeh i do i have 2 i have a set of sockets at the top and a set of sockets and the bottom also because of my case i have a set of sockets on top of my case itself.

---

### Post by P4man on 2009-10-28
To make life easier, chose one. If you are using the soundcard, then disable onboard sound in the bios. If you want to use the onboard sound, then remove the soundcard, even if temporarily. Once we get it working you can reenable to other one.

BTW, you dont want OSS. Its obsolete and doesnt support simultaneous playback. You really want pulseaudio.

---

