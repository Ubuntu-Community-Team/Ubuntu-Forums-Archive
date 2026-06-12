---
title: "Platronics Headset Issue"
date: 2009-10-15
forum: General Help
---

### Post by Revenga on 2009-10-15
I'm a new Ubuntu user, and I'm having trouble getting my Platronics Headset to work. The computer recognizes it, and I can see it in the volume control, but I have no idea how to make it work.

I can control the volume from my headset controls, but I can't hear any sound from my headset or record anything on Skype.

Thanks in advance!

---

### Post by P4man on 2009-10-16
Bluetooth audio is still a bit of a mess. I heard its much improved in Karmic (which will be released in a few weeks).

Anyway, you could try this:
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Note at the bottom it says it won't work with Skype. However, the latest version of skype (available on the skype website, and still in beta) claims to have fixed bluetooth issues, and the above howto predates that version, so perhaps it does work now, but don't bet your life on it.


**edit**: Im assuming you have a bluetooth set here, per perhaps you don't. Can you clarify first perhaps if you got a normal (wired) headset or a wireless bluetooth one?

---

### Post by Revenga on 2009-10-16
Sorry, I forgot to clarify that it's a USB headset.

---

### Post by P4man on 2009-10-16
Oh ok.

In Skype, in settings of audio devices, do you have a "USB audio" option for input and output ? If so, try it.  although having that option means you dont have the latest Skype (beta) which finally supports pulseaudio, and its probably best you grab a newer copy of Skype from Skype website.

If you only have "pulseaudio" there as option, then you got the latest beta of skype (which is good) but then we need to configure it elsewhere.

Im on karmic right now, and Skype less, so i cant give exact names or descriptions, and it might be slightly different, but if you got the latest skype, try  this; first install some additional pulse audio tools which ought to be installed anyway IMHO. Open a terminal and type 
```

sudo apt-get install pavucontrol padevchooser
```

Try will install pulseaudio volume control and device choser.

Once installed, play some music or something or launch a skype test call and then go to applications >  Sound and video > Pulse Audio Volume control. You should be able to select your USB headset there and "move" audiostreams for both playback and recording.  Im not sure how you want to configure it (have everything play on the USB set, or only skype, or play on both, or only on the headset if its plugged in) but you can configure all that and more with pulseaudio.

---

### Post by Mortus Pryde on 2009-11-01
I to am having issue with Karmic, the latest Skype version and a Plantronics USB Headset (DSP550). It is working, I am right now voicing VIA SecondLife, but it seems to be an ALSA device and Skype only seems to allow use of PulseAudio.

Any help is greatly appreciated.

---

### Post by P4man on 2009-11-01
Pulseaudio is a framework on top of alsa. If it works as a alsa device it should work with pulse. install pavucontrol and padevchooser and use those to redirect the input and output of skype to your bluetooth set. Have skype running with a test call and it should show up in PA device choser.

---

### Post by Mortus Pryde on 2009-11-01
Okay, so now I supposedly have all Skype sound and voice going to the headset, and recording now works to...

NOW! How do I get Skype sounds thought my speakers and still have voice through my headset.

I also wish to reiterate as the OP has as well, we are using USB Headsets not Bluetooth.

I have to say though this seems a totally *** backwards and Vista way of doing things... Meaning it only half works all the time and completely works half the time. I do hope the skype crew fix the pulseaudio implementation so that you can select the individual devices as desired.

IE.

Voice Playback -> Plantronics USB Headset
Voice Record -> Plantronics USB Headset
Sounds -> Internal Audio Device AKA Speakers

---

### Post by P4man on 2009-11-01
current version of skype for linux doesnt let you do that afaik. i read a trick somewhere to make it do that, but I didnt bookmark it nor do I remember how it was achieved. If you search long and hard you may find it though (on this forum, less than a month ago, and I probably posted in it)

What you can do fairly easily is have sounds play on both speakers and usb by using the padevchooser and configuring simultaneous output for local soundcards. But then you'd have conversations on your speakers as well as on the headset.

Alternatively you can search for the previous version of skype which used alsa instead of pulse and let you select a different device for ringing and speech.

> 
I also wish to reiterate as the OP has as well, we are using USB Headsets not Bluetooth.

thanks for clearing that up. I was already impressed by the fact you got bluetooth audio to work :)

---

### Post by Mortus Pryde on 2009-11-01
I am sorry but...

First of all YES it could do that as that was how I had it set up when I was using Jaunty. It was really easy and done DIRECTLY in Skype.

Second let me state this again! We are NOT! using Bluetooth headsets! We ARE! using USB headsets. Wired USB Headsets.

Sorry if I seem snippy, but both myself and the OP was fairly specific on this point, though it may be semantics, it also may not be, and thus we are specific about it so we can get accurate help.

---

### Post by P4man on 2009-11-01
> **Mortus Pryde said:**
> I am sorry but...

First of all YES it could do that as that was how I had it set up when I was using Jaunty. It was really easy and done DIRECTLY in Skype.


Its not karmic vs jaunty that makes the difference, but the new skype beta which uses pulse by default (leaving all the configuring up to the OS). As I said you might have more luck with the previous skype.

---

