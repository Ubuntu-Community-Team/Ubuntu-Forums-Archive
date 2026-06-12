---
title: "Thunderbird plays system wav files, but not mine. What gives?"
date: 2009-07-28
forum: General Help
---

### Post by ddixonr on 2009-07-28
All I want to do is play a wav file for email notifications. It is a wav file less than a second long I found online. I entered TB prefs, browsed for the file, but it wouldn't play. It plays with every other media player including within Nautilus. I tried an Ubuntu system sound from /usr/share/sounds, and it played perfect. I tried several more systems sounds, all great. I sudo cp'ed my wav into the system folder, and that didn't work. What gives?

---

### Post by philinux on 2009-07-28
Got a link I'll try it here.

---

### Post by ddixonr on 2009-07-28
[http://simplythebest.net/sounds/WAV/sound_effects_WAV/sound_effect_WAV_files/whistle_2.zip]("http://simplythebest.net/sounds/WAV/sound_effects_WAV/sound_effect_WAV_files/whistle_2.zip")

---

### Post by ddixonr on 2009-07-28
Update: I copied the system wav from /usr/share/sounds... to ~/Documents folder. Browsed to Documents in TB prefs, and selected the system wav. It plays. So I figured it must be something to do with the way that the wav files are created. I checked the properties of the system wav.- Uncompressed 16-bit pcm audio, stereo, 22050 hz, n/a bitrate. I opened up audacity, completely butchered the wav I wanted to use, but it now has identical properties to the system wav. Selected it in TB, but it STILL wouldn't play. This is crazy!

---

### Post by ddixonr on 2009-07-28
Last Update (solved): My file was too short- less than a second. Apparently TB doesn't like that. As of lately, ubuntuforums helps by letting me work it out. I guess I can't complain.

---

