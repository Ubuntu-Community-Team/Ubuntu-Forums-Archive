---
title: "How to get a bluetooth headset to work with PulseAudio (perhaps even Skype)?"
date: 2009-10-26
forum: General Help
---

### Post by mortti on 2009-10-26
I just got myself a Nokia BH-105 Bluetooth headset which I already have been able to establish parity with Karmic.

The question is if anyone knows how should I proceed in order to get the headset work as a audio device? PulseAudio (with newest updates) doesn't seem to automatically understand the device as such and therefore it doesn't work with Skype (2.1).

Do I need to make manual configurations concerning modules in Pulse or maybe something completely else?

I have the same problem also with Jaunty, but it might be a lot different as i've understood that it uses different bluetooth software and Pulse doesn't have the same features...

---

### Post by Nostalos on 2009-10-26
Mine is "ok" out of the box.  have a pair of Sony DRBT-22 headphones.   Assuming you are using Gnome for a desktop (sorry, have not touched KDE in a long while) you should be able to go to 

System -> Preferences -> Sound


then on the input/output tabs set your headset as the default input/output on each tab (provided you have paired them with the system already.


if it is a stereo headset that has both a2dp and "handsfree" profiles you will need to install padevchooser and switch the device in pulse from the "volume control" interface.  By default mine came up in handsfree instead of a2dp for stereo sound.   

I have had it working in pulse easiliy then, but find the sound quality to be severely lacking.

---

### Post by mvalenti on 2009-10-28
Not sure if this helps, but it helped me.... 

[http://ubuntuforums.org/showthread.php?t=1297828](http://ubuntuforums.org/showthread.php?t=1297828)


-Mark

---

### Post by dj-toonz on 2009-10-28
Here's how I got all of my A2DP devices working under Jaunty but the same thing works under Karmic


1) update pulse audio to 0.9.15 **don't Know if you have to do this under Karmic**

2) install blue man, Works way better then Gnome-Bluez IMO (has more features then Gnome-Bluez) like being able to use audio devices better & using blue-tooth modems with network-manager easier for example) 

3) install gnome-volume-control-pulse

Right Mouse click gnome-alsa volume control icon on the notification area & choose remove from panel as you don't need it with using the pulse audio volume control


4) install padevchooser **Pulseaudio Device Chooser**

restart gnome desktop to get the pulse volume control icon & the blueman Blue-tooth icon to show up properly

Pair the Bluetooth devices in Blueman normally


Open up Pdavchooser **pulseaudio Device Chooser**

it puts a icon in the notification area as a jack lead, if you left mouse click on the new icon, it comes up with loads of options

What you can do in the Pulseaduio Device chooser, If you option up Volume Control, if you right mouse click on the application what's playing the sound, it comes up with a menu 1. move stream 2. terminate stream (kills the music) so If I want to listen to the music via the HI-FI, I just right click on the stream in say Audacious in the volume control & move stream to my Nokia A2DP dongle for the HI-FI & music mutes on the desktop & starts streaming via the HI-FI speakers or I can do the same with my stereo headset or hands-free device

If you want to transfer the sound before you start the application, all you need to do is left mouse click on the Jack icon in the notification area & choose default sink (the picture of headphones) mines got 5 devices showing. 1) default - will always be your sound card device 2) other - so you can add the output device manually 3) my Nokia blue-tooth hands-free (what I use for Skype or VoIP) 4) my Motorola A2DP stereo, head-set for background music & a Nokia A2DP blue tooth reviver to Hi-FI to listen via big big speakers, just click on the device you want to listen via & from then all sound will be transferred to the blue-tooth device

If you don't want to have to keep opening up PdvaChooser & it going to the notification area all the time, just to use it , left mouse click on the Jack lead & open up preferences & enable  Start Applet on session Login

Right now I've got the Skype ringer (if I get a call coming in) being sent to my Hands-free device & a shout cast radio station being played out of my HI-FI speakers (all on separate streams off cause) & using a program called ear_candy to automatic fade & mute & pause the playback of different streams, Say I get a call coming in skype it starts ringing in my right ear & I press the button to accept/end the call on the hands-free device, ear candy Mutes/Pauses the sound coming out of the HI-FI speakers or desktop speakers & starts the sound playing again once I've finished with the call. It's the same if I'm using the Motorola stereo headset as that's got a built in microphone (and I'm having all the streams using that) ear candy will mute/pause the music/video sound Or whatever & let the Skype call though & then resume the other sound when the calls ended) 

Shame we have to have these programs running to do what we need, why cant gnome have them as default in the volume control applet with a visual effect of the sound like Vista & windows 7 has, I've got it like that now by doing all of the above

Edit, The version of Skype I'm using is the new Beta & it works grand with Pulse-Audio for me

About Blue-man & How to install it go here [http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html)
About ear candy & How to install it go here [http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html#more-1755](http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html#more-1755)

A Couple of screen-shots to go with the post

---

### Post by nidelius on 2010-06-12
The padevchooser helped me! Thanx!!

---

