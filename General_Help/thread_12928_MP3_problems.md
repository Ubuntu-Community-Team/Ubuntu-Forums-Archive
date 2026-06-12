---
title: "MP3 problems"
date: 2005-01-27
forum: General Help
---

### Post by JnnY on 2005-01-27
Hi there!

I just reinstalled Ubuntu, and suddenly I'm not able to play mp3's.
When I reinstalled, I first installed Xmms, and xmms-mad (as I also did last time).
But today when I logged in, it doesen't work...
I can browse and find the mp3's (they'r on a FAT32 partition), but the player just plays them really fast (everything works as it should, just a LOT faster), and with no sound (yes, system sound works). I have tried to log in and out with no result.

Is there anyone out there who can helt me? Frustrating not beeing able to listen to music :(

---

### Post by phend-one on 2005-02-15
Yes, I have the same problem too, where the mp3 plays fast, and would appreciate any help!

---

### Post by Buffalo Soldier on 2005-02-15
JnnY, does the same problem happen when using Rhthymbox?

---

### Post by phend-one on 2005-02-19
The problem occurs on any music player I try. XMMS and Rhythmbox.

I have also copied the mp3s from a FAT32 Partition!

---

### Post by kassetra on 2005-02-19
It's not your mp3s that are the problem, nor is it any of the players.
 
 The problem is in the sound driver.
 If you are using the Alsa sound driver sometimes what happens is that the default clock rate is set at 48Khz instead of 44.1Khz -- in order to fix the problem, you'll need some alsa tools installed:
 start with alsa-utils and and gnome-alsamixer, found in synaptic (should be regular warty universe repositories), and try to adjust the rate from there.
 
 Let me know if that doesn't work for you.

---

### Post by phend-one on 2005-02-20
Hmm I'm new to the whole Linux thing, so please bear with me!

I'm using Ubuntu Hoary, and I have ALSA installed ( 1.0.8 ) as well as alsa-utils. 

Problem is: I don't know which sound <insert word> (driver?) it's using? 
I go to System > Preferences > Multimedia Systems Selector and set everything to ALSA. (Defaults were ESD and OSS respectively)

When I try to play anything in Rhythmbox, it just says: "ALSA device "default" is already in use by another program." and "Could not pause playback."

If I change back to the default ESD/OSS, everything plays, but is super fast!


AHhhh!
*tears out tufts of hair!*
Help please!

---

### Post by Buffalo Soldier on 2005-02-20
phend-one,

Hoary is not for newbie, it is still in beta (development). Just out of curiosity, why didn't you install Warty?

---

### Post by kassetra on 2005-02-20
[QUOTE=phend-one]
 If I change back to the default ESD/OSS, everything plays, but is super fast!
 [/QUOTE]
 
 Ok, I need to see the output of a command, so please type this in a terminal and tell me what it says:
  ```
sudo lsmod |grep audio
``` 
 
 (don't worry, just hang in there with me, we'll get it.)

---

### Post by phend-one on 2005-02-20
Ahh! 

There is no output when I type the command: "sudo lsmod |grep audio"

Is there something wrong?

---

### Post by kassetra on 2005-02-20
[QUOTE=phend-one]Ahh! 
 
 There is no output when I type the command: "sudo lsmod |grep audio"
 
 Is there something wrong?[/QUOTE]
 
 Not yet that I can see, I was testing to see if the "audio" module may have been messing with your sound... ok, some more tests here:
  ```
sudo lsmod |grep snd
``` 
 
 also, do you happen to know what kind of soundcard you have?

---

### Post by phend-one on 2005-02-20
[QUOTE=Buffalo Soldier]phend-one,

Hoary is not for newbie, it is still in beta (development). Just out of curiosity, why didn't you install Warty?[/QUOTE]

I had Warty installed, and then tried to fix my sound, but after reading some things on forums and having a recommendation from someone in IRC, I needed a 2.6.10-3 kernel which would allow me to have ALSA-drivers1.0.8. This should have fixed my sound, but it didn't.

I currently use a Chaintech AV710 sound card. It's based on a Envy24 chip. Linux recognizes this as "ice1724." So far I've been unsuccessful with trying to get sound to work properly. A 'lspci' gives me:
0000:02:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
which leads me to believe I don't have a ice1724, contradictatory to what everyone says? I also tried to make sense of what was going on in this page: [ice1724 - AlsaOpensrcOrg](http://alsa.opensrc.org/index.php?page=ice1724). This page had some instructions about my specific card, but I was not knowledgeable to understand what they were trying to do.

I found this thread which had a asound.state and I followed the instructions. [(New asound.state for Chaintech AV-710!)](http://www6.head-fi.org/forums/showthread.php?t=106597). This is supposed to enable the "ALT Out" Jack which runs on the higher quality Wolfson DAC (2.1 only). I don't have a clue what the asound.state does.


If it answers your question more directly, I'm just curious about Linux is all. I want to see how well Linux can do for me, and I also like to experiment. I want to give Linux a chance before I turn away and say it wasn't for me. I am quite proud of myself for getting to install it and play with it, but I want to have sound and watch a video clip, mostly things I do normally around Windows. 

Sorry for being long-winded and taking over the thread.  :-P

---

### Post by phend-one on 2005-02-20
Sorry for posting multiple times in a row.

Output of 'sudo lsmod |grep snd':

snd_ice1724            53540  2
snd_ice17xx_ak4xxx      3936  1 snd_ice1724
snd_ac97_codec         74144  1 snd_ice1724
snd_pcm_oss            52132  0
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  4 snd_ice1724,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd_page_alloc          9732  1 snd_pcm
snd_ak4xxx_adda         5888  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_mpu401_uart         7680  1 snd_ice1724
snd_rawmidi            24480  1 snd_mpu401_uart
snd_seq_device          8460  1 snd_rawmidi
snd                    55012  11 snd_ice1724,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4xxx_adda,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10016  2 snd


The sound card is: Chaintech AV-710 as stated in my previous post. A more detailed explanation of what I'm trying to do is there.

Thanks!

---

### Post by kassetra on 2005-02-20
nuts!  you don't have snd-seq-oss!
  
  ok, do this:
   ```
sudo modprobe snd-seq-oss
```

---

### Post by phend-one on 2005-02-20
Okay, 'sudo modprobe snd-seq-oss' is done.

Here is 'sudo lsmod |grep snd' again:

snd_seq_midi            8512  0
snd_seq_oss            34176  0
snd_seq_midi_event      7424  2 snd_seq_midi,snd_seq_oss
snd_seq                52528  5 snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_ice1724            53540  1
snd_ice17xx_ak4xxx      3936  1 snd_ice1724
snd_ac97_codec         74144  1 snd_ice1724
snd_pcm_oss            52132  0
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_ice1724,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  2 snd_seq,snd_pcm
snd_page_alloc          9732  1 snd_pcm
snd_ak4xxx_adda         5888  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_mpu401_uart         7680  1 snd_ice1724
snd_rawmidi            24480  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8460  4 snd_seq_midi,snd_seq_oss,snd_seq,snd_rawmidi
snd                    55012  12 snd_seq_oss,snd_seq,snd_ice1724,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ak4xxx_adda,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10016  2 snd

Is the command you got me to type part of the alsa-drivers1.0.8 ./configure before the make, make install? (./configure --with-cards=ice1724 **--with-sequencer=yes**)

---

### Post by kassetra on 2005-02-20
[QUOTE=phend-one] Is the command you got me to type part of the alsa-drivers1.0.8 ./configure before the make, make install? (./configure --with-cards=ice1724 **--with-sequencer=yes**)[/QUOTE]
 
 No... but you need snd-seq-oss for everything to work properly...
 ok, run this command:
  ```
alsamixer
``` 
 
 And make sure it's not muted or anything... 
 then try your sound again.

---

### Post by phend-one on 2005-02-21
In 'alsamixer' which sliders am I specifically looking to change? Master and PCM?

Also, sound only works when the settings in Multimedia Systems Selector are:
Audio Tab:
Default Sink
Output: ESD
Pipeline: esdsink

Default Source:
Input: OSS
Pipeline: osssrc

Under these settings, mp3s play at fast speeds where it sounds like "chipmunks."


When both of the above settings are set to ALSA, I get:
"ALSA device "default" is already in use by another program." and "Could not pause playback" errors.

Any idea what needs to change?

---

### Post by kassetra on 2005-02-21
ok, we're almost there...
  do you have a file called /etc/modutils/alsa?
  
  If you do, add the following to the end (if it's not already there), and if not, create a new file in /etc/modutils called alsa
   ```
# ALSA portion
          alias char-major-116 snd
         alias snd-card-0 snd-ice1724
 	# module options should go here
 
         # OSS/Free portion
         alias char-major-14 soundcore
         alias sound-slot-0 snd-card-0
 	
 	# card #1
 	alias sound-service-0-0 snd-mixer-oss
 	alias sound-service-0-1 snd-seq-oss
 	alias sound-service-0-3 snd-pcm-oss
 	alias sound-service-0-8 snd-seq-oss
 	alias sound-service-0-12 snd-pcm-oss
  
```

---

### Post by phend-one on 2005-02-21
Okay, didn't have the /etc/modutils/alsa file, so I:
'sudo gedit /etc/modutils/alsa'
pasted the contents and saved.

Hope I did this right.

---

### Post by kassetra on 2005-02-21
[QUOTE=phend-one]Okay, didn't have the /etc/modutils/alsa file, so I:
 'sudo gedit /etc/modutils/alsa'
 pasted the contents and saved.
 
 Hope I did this right.[/QUOTE]
 
 sounds like you did it right.  reboot & try your sound.  (and cross your fingers that I've nailed down all the problems -- but if not, I have more stuff to do.)

---

### Post by phend-one on 2005-02-21
Hmm... gave the box a reboot, and sadly the sound is still playing at a fast speed. :? 

I read up there might be a problem with ESD and how the sounds are being played in a music player?

I did a quick test in totem (xine) and the video does not match with the audio. Someone in these forums also reported a temporary solution to this, which was 'killall esd'. This solved all of his sync problems in totem, but he couldn't hear the ubuntu sounds unless he rebooted.

Could this be a problem with the Multimedia Systems Selector? They are still set at ESD/OSS.



**EDIT #1:** Okay, I finally found what you were referencing to with the 48kHz and 44.1kHz, however now the music plays at a regular speed, but is filled with static and  crackling.

---

### Post by kassetra on 2005-02-21
[QUOTE=phend-one]**EDIT #1:** Okay, I finally found what you were referencing to with the 48kHz and 44.1kHz, however now the music plays at a regular speed, but is filled with static and crackling.[/QUOTE]
 
 That's the alsa output giving you crackling?

---

### Post by phend-one on 2005-02-21
How do I know if it's ALSA, ESD or OSS?

---

### Post by kassetra on 2005-02-21
[QUOTE=phend-one]How do I know if it's ALSA, ESD or OSS?[/QUOTE]
 
 Try playing something in xmms -- and changing the output from alsa, to esd, to oss...   That way you'll know exactly which driver is causing the crackling.
 
 On my system, if I play any music or movies through alsa, it crackles.

---

### Post by phend-one on 2005-02-21
Did the following before rebooting:
1) System > Preferences > Sound : Turned off 'Sound server startup'
2) 'gstreamer-properties' (which is the same as 'Multimedia Systems Selector') and then changed both sink and source to ALSA.

Did a reboot, and in XMMS / Rhythmbox, (using ALSA), I noticed that increasing PCM volume increased the amount of crackling. The default was 48, and I slowly increased to 100, to find more and more distortion. Also, I had to reset the rate from 48kHz to 44.1kHz (the settings before didn't stick).

---

