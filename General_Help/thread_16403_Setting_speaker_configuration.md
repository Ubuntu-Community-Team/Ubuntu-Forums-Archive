---
title: "Setting speaker configuration?"
date: 2005-02-21
forum: General Help
---

### Post by J-Doe on 2005-02-21
In windows there is a possibility to set speaker output configuration so the system knows how many channels to send the audio to. In windows environment I used Hercules's own audio drivers and control panel from which it was easy to change from normal 5.1 speakers to headphones....
Currently my audio "works" in Ubuntu but the sound only comes from the front speakers, rear speakers and subwoofer are silent... So what do I have to do to get audio form all of my speakers and can I get that speaker configuration control panel somewhere? 

I still can't start to use ubuntu before this problem is solved, so please help!

---

### Post by J-Doe on 2005-02-23
So this kind of sollution just doesn't exist, nobody knows it or just aren't willing to tell it to me? :-)

---

### Post by Yukonjack on 2005-02-23
Open the the volume control and you can set it in there, you should have all the choices for surround, 4 speaker ect... Most of the setting will be mute by default.

---

### Post by J-Doe on 2005-02-23
Is there a subwoofer control somewhere?

---

### Post by Yukonjack on 2005-02-23
[QUOTE=J-Doe]Is there a subwoofer control somewhere?[/QUOTE]

Do you have Alsa Mixer install? 
Also do you use an external amp?

---

### Post by J-Doe on 2005-02-23
yes I have alsamixer installed... 
and my 5.1 speakers are connected to this external control-box (which is of course connected to the soundcard). This control-box does have volume controls but their are pretty much useless. My speakers & the box are like the cheapest model available and those volume controls can't set the volume level high enough... so if I can't turn up the subwoofer's volume from the computer, it's pretty much silent...(actually though these are the cheapest model the subwoofer is pretty good, that control-box just sucks.) :razz:

---

### Post by Yukonjack on 2005-02-23
Well I don't see one just for the subwoofer, I use an Altec Lansing 5.1 and works great, you might try increasing the bass and max out the pcm feature this might work for you but I have no experience with the sound card you are using. Maybe someone with your setup will show up. Give it a little bit of time.
Sorry I could not be of more help.

---

### Post by J-Doe on 2005-02-23
My soundcard is Hercules Fortissimo III 7.1 (or something like that)... I tried pretty much every slider that volume control has and can't really find one that would increase bass...
Anyone with Hercules soundcard out there? :)

---

### Post by ow50 on 2005-02-23
Speaker settings is one of the most important things missing in ubuntu for me. I have 5.1 speakers and a sound blaster audigy card. The volume control worked fine and I could get sound out of all speakers right after installing, but the problem was, that it wasn't suitable for a 5.1 system.

For 5.1 systems, the bass should be redirected to the subwoofer, so that no bass comes out of the satellite speakers. Playing bass through the satellite speakers of a cheap 5.1 system will sound very nasty.

I had to install emu-tools, which gives some settings for sound blaster cards, most importantly 'route all to sub' -setting. Installing emu-tools was a great pain, I even had to edit the source code to get it to compile on a modern compiler. Unfortunately other sound card manufacturers might not have bothered to make such configuration apps for linux.

I also noticed that the subwoofer volume was much lower than in windows. This was quicly solved by turning the volume knob up at the back of the subwoofer.

So now everything works good, but it took a long time to figure out how set it up right.

-----------------

You should have in the gnome-volume-control the following:

pcm center
pcm front
pcm lfe
pcm surround
surround
center
lfe

Do you have those sliders? Are they all unmuted?

---

### Post by Calle on 2005-04-20
[QUOTE=ow50]You should have in the gnome-volume-control the following:

pcm center
pcm front
pcm lfe
pcm surround
surround
center
lfe

Do you have those sliders? Are they all unmuted?[/QUOTE]
I've got the same problem as the thread starter, I've got 5.1 surround speakers, but only the left and right is pumping out sound, the others are silent. I tried to look for pcm center, front, lfe, surround [and so on], but I couldn't find any of those.
Do I have to install another package?

Edit: I found the sliders, but still I only hear sound in the left + right speaker. I've tried in 5-6 different media players.

---

### Post by CrustyDOD on 2005-04-26
I have Audigy2 ZS and 5.1 system also and on my volume control i have to move sliders for these:

Front
Center
Surround
LFE

Muting and unmuting PCM "same_name" doesn't give any effect for me.. so try also with those without PMC in front of the name..

---

### Post by Happy on 2005-05-03
I seem to be having the reverse problem...
I'm getting sound but I can't seem to control it except via the knobs on my speakers.
I'm using the digital jack of a Sound Blaster Live!Value connected to Boston speakers.

None of the Playback volume controls do anything...

---

### Post by bluemax on 2005-05-20
I'm having the same problem, but in Hoary. I have a Hercules Fortissimo II card, and can't get sound out of anything but the front speakers. Can't even get anything out of my headphones, either. I've resorted to plugging my headphones into the 'front speakers' jack whenever I want to use them.  :roll:

---

### Post by Laemel on 2005-12-24
I know this is an old thread, but I've been having the same problem in Breezy and couldn't find a solution by searching the forums, so I'm going to post my solution here for people who are searching....

What I needed to do in order to get 2-channel stuff like music to play on my subwoofer and center/surrounds was open the volume control, go to Preferences, and enable the "Wave Center", "Wave Surround", and "Wave LFE" sliders and turn them up (I have a Sound Blaster Live 5.1 by the way).

---

### Post by Hasen_A on 2007-01-24
> **ow50 said:**
> You should have in the gnome-volume-control the following:

pcm center
pcm front
pcm lfe
pcm surround
surround
center
lfe

Do you have those sliders? Are they all unmuted?

All I have is one PCM. I am using a Fortissimo III and Gome-Volume-Control is version 2.16.1
Any tips?

---

### Post by porcupine_monkey on 2007-10-02
Have you tried enabling them through Edit -> Preferences?
There should be a checked listbox, where you can pick which controls to show.

---

### Post by Hasen_A on 2007-10-02
yes but the I don't think that the software support for the card is very good.

---

### Post by sneax on 2007-10-02
The problem is that you are all trying to play a stereo file (an MP3 or whatever), obviously this audio source only has data for front left and right speakers and thus only those speakers will have sound.

If you want multichannel sound you either have to play a multichannel audio source (try find some multichannel OGG file?).

In Windows there is a system that will upmix a stereo signal to all 4 speakers, I don't think such a system exists by default in linux. Creative has such a 'system' too which is called CMSS. That's the reason why you get multichannel in windows by just playing a stereo file.

---

