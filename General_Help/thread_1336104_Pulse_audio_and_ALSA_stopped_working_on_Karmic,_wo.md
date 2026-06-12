---
title: "Pulse audio and ALSA stopped working on Karmic, work only as root"
date: 2009-11-24
forum: General Help
---

### Post by miro85 on 2009-11-24
Hello,

my sound stopped working a few days ago. However, if I log in as root all works fine. When I set the output(not as root) in audacious to OSS it starts working immediately but on pulse(default) or ALSA it doesn't work. Also, when playing a video in totem or mplayer, I get internal gstreamer error:negotiation problem. I tried reinstalling all gstreamer codecs but it doesn't help. I have a fresh install of Ubuntu 9.10 and it was working fine for 2 weeks on a thinkpad r52 with an Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller. I'm not sure what I changed in the last few days, I installed some hdaps tools with tp_smapi for hard drive active protection(software for thinkpads) and installed a few games. I had to restart during the installation of one of the games and I had a few broken packages but that was fixed later. Any ideas?

EDIT: I ran fsck for some unrelated reason and now there is no more "internal gstreamer error:negotiation problem"

---

### Post by renkinjutsu on 2009-11-24
try this ```
sudo usermod -a -G audio YOURUSERNAMEHERE
```

then, log out and back in

---

### Post by miro85 on 2009-11-24
I tried it but it still doesn't work.

---

### Post by renkinjutsu on 2009-11-24
can you post the output of ```
ls -l /dev/audio*
```

just checking the ownership/groups of the audio devices

---

### Post by miro85 on 2009-11-24
Here it is:

crw-rw----+ 1 root audio 14, 4 2009-11-24 11:08 /dev/audio

---

### Post by renkinjutsu on 2009-11-24
that is odd.. you did log out and back in, after issuing that command i gave earlier, right?

try doing this to see if you get any sound

```
cat /dev/urandom > /dev/audio
```
press ctrl+c to stop it

---

### Post by wojox on 2009-11-24
```
sudo chown -R $USER:$USER ~/.pulse
```

---

### Post by miro85 on 2009-11-24
I logged out and in after the command, I also added my user name to the audio group in Users&Groups in the System-Administration menu earlier today, and the root isn't part of the audio group, I don't know if it matters. When I issue the last command I hear white noise or something like that. Also, thank you very much for the quick replies.

---

### Post by miro85 on 2009-11-24
I tried the sudo chown command but nothing seems to happen, I logged out and in and it still doesn't work.

---

### Post by miro85 on 2009-11-24
I'm giving up, I'm just going to reinstall ubuntu, it will take me less time than to find out what the problem is.

---

### Post by renkinjutsu on 2009-11-24
> **miro85 said:**
> I logged out and in after the command, I also added my user name to the audio group in Users&Groups in the System-Administration menu earlier today, and the root isn't part of the audio group, I don't know if it matters. When I issue the last command I hear white noise or something like that. Also, thank you very much for the quick replies.

Yeah, the command was supposed to give you white noise.. That was just to check if your audio was working.. and it was.

---

### Post by miro85 on 2009-12-01
I reinstalled ubuntu, all was going well for a few days but now I don't have sound once again. This is driving me crazy. Can I set the whole system to use OSS? Would that be a solution to my problem? If anyone has any ideas at all please let me know.

---

### Post by iamgeniusrnti on 2009-12-01
> **miro85 said:**
> I reinstalled ubuntu, all was going well for a few days but now I don't have sound once again. This is driving me crazy. Can I set the whole system to use OSS? Would that be a solution to my problem? If anyone has any ideas at all please let me know.
 
You're not alone, same thing happened to me and another guy on here. Beyond the usual troubleshooting of the audio group, no one has found out why.  I wound up doing a apt-get --purge alsa and then reinstalled.

Alsa still doesn't work but it but at least now it falls back to OSS. I can get sound when I go to youtube or run an app.  But my bootup sounds and systems sounds don't work even with OSS running.
 
When I run alsamixer it comes up with a wierd error: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

I mentioned this problem twice before, but as soon as I mention that error the thread goes dead.  Guess I stumbled on a bug that's never been discovered.  HAHAHA!

---

### Post by miro85 on 2009-12-01
I guess one solution is to run as root all the time, but it's not the best one. 

Can you tell me exactly how to purge and reinstall ALSA, I wanna give it a shot. My log in and system sounds are turned off anyway so that wouldn't be a problem. I can run alsamixer just fine, everything seems to be ok there. 

If nothing works I'll reinstall ubuntu again and then install one program at a time to try to find out at what moment exactly the sound stops working.

What are your computer specifications?

---

### Post by miro85 on 2009-12-01
Now the sound works all of a sudden and I didn't even do anything. I logged in as root a couple of times but nothing more. Got no idea what's going on... I'll post if I find out anything.

---

### Post by iamgeniusrnti on 2009-12-01
> **miro85 said:**
> I guess one solution is to run as root all the time, but it's not the best one. 

Can you tell me exactly how to purge and reinstall ALSA, I wanna give it a shot. My log in and system sounds are turned off anyway so that wouldn't be a problem. I can run alsamixer just fine, everything seems to be ok there. 

If nothing works I'll reinstall ubuntu again and then install one program at a time to try to find out at what moment exactly the sound stops working.

What are your computer specifications?

Asking a newb for a command is probably not in your best interest--I believe I used #apt-get remove --purge alsa.

And then apt-get install alsa.

The box giving me the sound issue is an Acer D250 Netbook.

---

### Post by Mark_in_Hollywood on 2009-12-16
> **renkinjutsu said:**
> try this ```
sudo usermod -a -G audio YOURUSERNAMEHERE
```

then, log out and back in

I confirm that the above solution worked on Xubuntu, for VLC.

I cannot listen to (hear) the Apple vs. PC commercials, nor stories at cnn.com.

---

