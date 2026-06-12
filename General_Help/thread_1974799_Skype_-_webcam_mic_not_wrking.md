---
title: "Skype - webcam mic not wrking"
date: 2012-05-06
forum: General Help
---

### Post by motorcity909 on 2012-05-06
Hi 

I've got a webcam with a built in microphone.  The mic works fine if i record on Audacity but in Skype the mic doesn't work, although video on Skype is fine.

I've got the USB mic selected in the sound settings - see screenshot1.

In Skype > Options > Sound Devices, there is only the Pulse Audio server to select - see screenshot2.

Interestingly , I've got a netbook also with Xubuntu 11.10 and its integrated webcam & mic works fine in Skype.

Any help as always is much appreciated.

Thanks
Da\/e

---

### Post by motorcity909 on 2012-05-07
Further info if it will help - when I run lshub, it shows the webcam as a Microdia MSI Starcam Racer

Same (unanswered) probelm here too - [http://ubuntuforums.org/showthread.php?t=1898589](http://ubuntuforums.org/showthread.php?t=1898589)

Thanks
Da\/e

---

### Post by LewisTM on 2012-05-07
Try this:
First install Pulseaudio volume control **pavucontrol** then launch it. 
In the Input Devices tab select the USB camera as your primary device and mute the left channel.

Cheers!

---

### Post by Kangarooo on 2012-05-07
WOuldnt it be better to finally integrate working fix then to make new users think about some pavucontrol

---

### Post by motorcity909 on 2012-05-07
Hi

I've installed pavucontrol and using the skype test call it successfully recorded my voice and played it back.  Webcam mic is only mono so no left channel to mute.

Now waiting to do a proper test call with my son (if he can tear himself away from Minecraft for two minutes....)

Cheers
Da\/e

---

### Post by motorcity909 on 2012-05-07
Hi again

All good!  Skype call to my son's Win7 laptop - working video & sound.

It's also fixed Google Hangouts which had the same issue - no sound from mic.

So, thanks to LewisTM for the solution - and agreement with Kangaroo that this kind of things should just be there from the off.

Cheers all
Da\/e

:-D

---

### Post by ganjajuanabud on 2012-05-14
I just installed Precise Pangolin. I Previously had Oneiric Ocelot. On both systems I had no success with the built-in mic on my Logitech webcam using skype. Once again, video fine and I can hear the other person's end. I noticed that Pangolin came with pavucontrol already (I had to install it on Ocelot before). I can see input using Audacity monitor, so it's getting through somewhere! I tried on Ocelot using Mixer and un-linking channels, lowering volume on one, etc. Can you suggest anything else I might try? I don't see how I can "select the USB camera as your primary device" so maybe we could start there? I was hoping with the new release that everything would "just work" but then I wouln't soon have learned anything, would I willl have?

---

### Post by LewisTM on 2012-05-15
I have a similar webcam with a similar problem. I'm not near that computer right now so from memory, try this:

1) Exit Skype
2) Connect your webcam
3) Go to pavucontrol/Input Devices
4) You should see the Webcam as one of the devices
Chances are you won't and this is the problem. So next:
5) execute 
```
pulseaudio --kill
pulseaudio --start
```
6) Look again the the Input Devices. Pulseaudio should have picked up the camera.
7) Start skype and try again.
EDIT
8: While recording, you might have to go to pavucontrol/Recording and pick the Quickcam as the input for Skype.

---

