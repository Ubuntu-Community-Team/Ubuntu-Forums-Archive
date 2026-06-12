---
title: "Skype issues, No sound with Pulse, distorted with esound"
date: 2010-12-05
forum: General Help
---

### Post by Vahkiti on 2010-12-05
Ok, I've been working at this issue myself for two days and still haven't come up with anything. On the default system config with Pulseaudio, Skype 2.1 has absolutely no sound, worse, if I call, or somebody calls me, the program becomes unresponsive and I end up having to either reboot or log out and in again. The only option Skype gives me in the sound settings for anything is PulseAudio Server (local) which, (obviously) is incorrect.

So after a few hours of trying to sort it out with pulse, I found a workaround involving the REPLACEMENT of Pulse with esound following these commands in a terminal:

> killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

This works to an EXTENT. I have output sound, Skype makes all it's little beeps and blips and what-have-you, I can hear the other person clear as day, and I'm able to select different sound card settings now. But when I talk to someone or call echo123, my voice comes through choppy, garbled and extremely distorted. Words are run together at a super fast pace, and sometimes even quickly repeat. 

So then I tried yet another supposed workaround, this involving modifying .asoundrc as seen here:

> #asym fun start here. we define one pcm device called "dmixed"
   pcm.dmixed {
	   ipc_key 1025
	   type dmix
	   slave.pcm "hw:0,0"
   }
   
   #one called "dsnooped" for capturing 
   pcm.dsnooped {
	   ipc_key 1027
	   type dsnoop
	   slave.pcm "hw:0,0"
   }
   
   #and this is the real magic
   pcm.asymed {
	   type asym
	   playback.pcm "dmixed"
	   capture.pcm "dsnooped"
   }
   
   #a quick plug plugin for above device to do the converting magic
   pcm.pasymed {
	   type plug
	   slave.pcm "asymed"
   }
   
   #a ctl device to keep xmms happy
   ctl.pasymed {
	   type hw
	   card 0
   }
   
   #for aoss:
   pcm.dsp0 {
	   type plug
	   slave.pcm "asymed"
   }
   
   ctl.mixer0 {
	   type hw
	   card 0
   }

After applying this, I not only changed my settings to asymed, but ALL the new settings it gave me. This time my words are run together AND I sound like some kind of deep voiced monster.

Now, once and for all, to save me another two days of searching through google and topics with unanswered pleas for help, can somebody tell me what is going on here and how the hell do I fix it? T_T

I'm running Skype 2.1, (latest build) on Xubuntu 10.10 with a C-Media CMI8738 sound card. Sound works on all other applications and the microphone is solid, since I just switched from Windows and it worked before now.

P.S. just to avoid people thinking I'm stupid and asking this, yes I am positive that none of the sound settings are on mute. XD

---

### Post by AOB on 2011-01-20
I have the same configuration except I use a Creative Soundblaster on a IBM Intel PIII processor and ASUS P2b-F motherboard. I loaded both also and pulseaudio. At the test call I hear the dialling tone then the ringing tone. Beyond that is soundless except I saw on the screen, speaking....then call duration.... I need help please help.

---

