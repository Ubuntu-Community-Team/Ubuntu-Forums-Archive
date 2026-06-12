---
title: "No Sound With Apps After OSS Install In Karmic? [[Semi-FIX]] Help still needed Guru's"
date: 2010-02-19
forum: General Help
---

### Post by charlesguzman on 2010-02-19
For Karmic users, I've heard many rumors that ALSA is causing problems. I haven't completely mastered using the OSS (open sound system) yet because of it's lack of graphical input (though their workarounds), but the biggest complaint I've seen is that after installing OSS in karmic (using the source), people aren't hearing sounds. 

I used this link to help me install OSS in my Karmic installation. [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) 

**Note:
For me, removing ALSA caused tons of problems for me and caused me to have to re-install Karmic so Just skip that part of the tutorial if you don't want to have to troubleshoot ALSA problems.

After following that installation guide, do a quick reboot.

Now you have to configure XMMS, VLC, and other apps you might use to use the Open Sound System (OSS). If you do not, you may be able to play files in these programs, but you will not hear any sound. For XMMS, I used the alternate sound directory /dev/dsp in order to get sound and for my VLC media player, I had to manually set it under advanced options to do the same. 

**Solution in a few quick words**
Configure your apps to use OSS. If you don't, you won't hear sound. :) Simple as that.

**Extra Info**

1) Because Karmic's volume applet uses ALSA/PulseAudio to do its work, you will not be able to use the handy little volume control interface anymore. Instead, use ossmix in the Terminal to adjust volume output settings. If you are hearing volume from your laptop speakers and your headphones, make an adjustment to ossmix using the command:
jack.int-speaker.int-speaker 0:0

2) I am really inexperienced compared to many Linux users. I'm truly a beginner, but am still learning. If there is a way to use the volume control applet, I'd appreciate your input in configuring the Karmic volume applet to use OSS instead of being based on Pulse/ALSA. As of now for me, moving the slider or using the laptop's built in buttons show's the volume changing on the screen, but no sound change happens. Having someone's input on this would be really nice. I have tried Dave Lentz's audio hacks, but don't know how to implement them. Thanks!

3) Comments and input is welcome! I am pretty new to Linux so forgive me for lack of details on my system. I know many Linux veterans get annoyed at this, but for this problem, I'm not sure what to list.

---

### Post by handy on 2010-02-19
No one likes to be yelled at.

Your title will put some people off, who would have otherwise come in & offered help.

Just a tip.

---

### Post by cariboo on 2010-02-19
Moved to General Help, as this is not a Cafe question.

Please don't use all caps in your thread titles. it is impolite.
BTW I edited the thread title too.

---

### Post by ETbluez on 2010-02-19
This might help 
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

