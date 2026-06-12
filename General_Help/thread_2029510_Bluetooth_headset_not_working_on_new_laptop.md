---
title: "Bluetooth headset not working on new laptop"
date: 2012-07-19
forum: General Help
---

### Post by Ingenium on 2012-07-19
So I just got a new laptop (Thinkpad T430) to replace my Thinkpad T400. I was running Ubuntu 12.04 on the T400 that I had upgraded through several releases of Ubuntu. On that computer, my Jawbone Icon headset works perfectly. I can use the Telephony Duplex (HSP/HFP) sound profile and it works as both an output and input device. I didn't do any special configuration to make this work, it just worked out of the box when I got the headset.

However, on the new computer, I paired the headset and the Telephony Duplex profile doesn't work. I get absolutely no sound on the headset, and the microphone registers no input. I changed HFP=false in /etc/bluetooth/audio.conf to match the T400 configuration, and now when audio tries to play the headset beeps to say it's reconnected, but then there's no audio. 

If I change it to the A2DP profile, then I get sound on the headset, but then the input option disappears. And it also doesn't drop packets when the signal degrades, meaning when I'm using it on Skype the audio slowly gets behind the video, to the point where if I walk to the other side of the room then the person has finished talking on the video before I even start to get the audio. Then I have to turn off the headset (or disconnect it) and reconnect to get it back in sync. So this isn't a work around. 

The new T430 has a Broadcom Bluetooth chip, showing up as:
Bus 001 Device 007: ID 0a5c:21e6 Broadcom Corp.

The T400 also has a Broadcom chip, showing up as:
Bus 004 Device 004: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II

Anyone have any suggestions?

---

### Post by EGA on 2012-07-29
I don't have a solution for your problem. Sorry, just asking out of interest: Is the built-in microphone working ootb (especially regarding Skype)?

---

### Post by cjohnston on 2013-03-11
Were you ever able to figure this out? I have an issue that seems to be the same on raring.

---

