---
title: "pulseaudio"
date: 2010-03-01
forum: General Help
---

### Post by rsteele1 on 2010-03-01
What's the deal with pulseaudio? I cant remove it and I cant get it to work. The GUI in System/Preferences is different in 9.10 from 8.10. I can't get Skype to work properly for starters and the sound is all garbled on everything else when it does work. Bring back ALSA and make pulse an option, at least until the bugs are worked out. I've googled my fingers off for 2 days and I have seen a lot of disatifaction with pulse. Most people are saying the same thing I am. I don't care how great the latency is or what it's supposed to do if I cant configure the sound server the way I want it.

---

### Post by darolu on 2010-03-01
Pulseaudio and ALSA work together; check all the settings at:
```
$ alsamixer
```

---

### Post by 3rdalbum on 2010-03-01
Skype gets the audio data straight from Pulseaudio, not from the device. So you must set your sound input and output devices in the Ubuntu volume control (right-click the volume control applet and choose Sound Preferences and make your choices from the Input and Output tabs).

---

### Post by rsteele1 on 2010-03-01
Mabey I should be more specific. Skype has three options for sound preferences. Mic,speakers,and ringing.After I installed Karmic they all say pulseaudio. I cant find an option in the system/sound preferences to change the output for speakers(ringing) and headset(listening). I can have one or the other but not both. If I select my speakers for output in sound preferences the conversation echoes on the other end and the conversation is anoying(hello...hello what wh.. I cant understand you...)If I select headset I cant hear the phone ring and I would rather not be teathered to my machine via my usb headset the entire time I am home. The previous version had a somewhat more useful interface for sound preferences and I was able to fix these problems but now it is gone. Again, I suggest reverting to ALSA as the default and making pulse an option untill it is fixed. Using the computer involves sight(video) and hearing(sound) .Without a reasonably useful.and easy to use sound server 50% of the computer is useless. Add to that Problems with sound not working with something like Flash,which is problematic in itself and used by countless websites, and you soon have a useless operating system. If anyone knows how to uninstall pulse and revert to alsa I and probably others would be very grateful. I've tried numerous suggestions with no success so far. HELP! Don't make me go back to windows.

---

### Post by alexandari on 2010-03-01
Wow don't go back to windows we can work this out hahaha.

ok you can try installing **esound** , and removing pulseaudio.

```
sudo apt-get install esound

sudo apt-get remove pulseaudio
```

---

### Post by rsteele1 on 2010-03-01
I tried the suggestion from alexandri(install esd, remove pulseaudio) now I dont have a desktop.

---

### Post by alexandari on 2010-03-01
what... O.o

Did pulseaudio remove other things as well? Like ubuntu-desktop...

---

### Post by rsteele1 on 2010-03-01
ok. got the desktop back. iused a live cd and then rebooted and its here.wehn i go to sound preferences it says Waiting fo sound system to respond.also no volume control on task bar, we're getting closer

---

### Post by alexandari on 2010-03-01
Ok so you say you have alsa installed also? Are there any choices in selecting Audio Output and Audio Capture and things like that in the sound preferences

---

### Post by rsteele1 on 2010-03-01
No. when I go to system preferences sound I just get a messege that says waiting on sound server. Missing volume control also. I do have sound and Skype seems to be working. Installed alsa mixer and alsa gui.BTW thanks for the help. I've never posted to the fourms before. This is awesome.

---

### Post by alexandari on 2010-03-01
> **rsteele1 said:**
> No. when I go to system preferences sound I just get a messege that says waiting on sound server. Missing volume control also. I do have sound and Skype seems to be working. Installed alsa mixer and alsa gui.BTW thanks for the help. I've never posted to the fourms before. This is awesome.


So it is working fine now? Sorry I'm a little distracted tonight,I can't think straight...

---

### Post by rsteele1 on 2010-03-01
Well, skype seems to be working and sound comes out of the speakers (log in , mouse click etc) I just dont have any control panel options in ubuntu for sound. Skype let me choose from a drop down list. Also the volume contro icon is missing from the task bar.When I get back home from work I can take a crack at it again.

---

### Post by rsteele1 on 2010-03-02
Back to square 1. I did a fresh install of Karmic (studio version) apt-get remove --purge pulseaudio, apt-get install esound. Rebooted and black screen. No desktop no login no nothing. Not even grub loading message. Back to my original post. Please take pulse out as the default and make it an option. The excuse that" it has to be there or the developers will never get the bugs fixed" doesn't cut it. Thats the MS philsophy.If a package is known to have serious bugs then it should NEVER be released without the option of successfully removing/disabling it.  Having said all of that,I seem to have 2 choices.1:Come up with some sort of custom install that doesn't use pulse or 2: Windows.

---

### Post by rnerwein on 2010-03-02
> **3rdalbum said:**
> Skype gets the audio data straight from Pulseaudio, not from the device. So you must set your sound input and output devices in the Ubuntu volume control (right-click the volume control applet and choose Sound Preferences and make your choices from the Input and Output tabs).

hi
thanks for that hint. i installed skype today - no microphone !
i just follow this instructions and ---> the microphone works and the speakers too !!!

have a nice day
ciao:D

---

### Post by methodtwo on 2010-03-03
rsteele1: I can't solve your specific problem. Pulseaudio is deeply embedded in gnome. However you still have choices:
I have Karmic netbook remix, 9.04 plain gnome and Debian with XFCE.
NBR drives a cute machine fast but it's definitely wobbly.
9.04 is smooth and nearly faultless on an HP with centrino duo.
Debian is bombproof on a 10-year-old desktop.
So it's horses for courses mate.
Enjoy.  ;^D

---

### Post by rsteele1 on 2010-03-03
Last night I did my n_th_ install using xubuntu. Pulse is present here also but it seems to be working correctly so far. I plan to keep looking at other distros and trying them out.
Distros come and go and  when developers insist on taking one in a direction that the community doesn't want they fall out of favor. I hope this doesn't happen with Ubuntu and the Gnome desktop because it seems to be the best supported with the most apps.For anyone who doubts that pulse is a problem may I suggest Google. Good luck to the dev team.

---

