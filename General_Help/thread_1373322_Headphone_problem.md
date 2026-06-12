---
title: "Headphone problem"
date: 2010-01-05
forum: General Help
---

### Post by ghostcamera on 2010-01-05
hey, ive been using ubuntu for a few days now and ive just figured out that i cannot use my headphones on my laptop correctly.

what i mean is when i plug my headphones into the jack on my laptop i get the sound coming from both the laptop internal speakers and the headphones.

i have looked at a few guides on the internet about going into alsamixer and "muting headphones" or something but there is just not an option for that for me.

my laptop is an advent 5401, i dont know much about the commands that can be done for the soundcard as im rather new to ubuntu.

im using ubuntu 9.10 if this helps.

help would be really appreciated as this is very annoying! thanks, dean.

---

### Post by Twitch6000 on 2010-01-05
> **ghostcamera said:**
> hey, ive been using ubuntu for a few days now and ive just figured out that i cannot use my headphones on my laptop correctly.

what i mean is when i plug my headphones into the jack on my laptop i get the sound coming from both the laptop internal speakers and the headphones.

i have looked at a few guides on the internet about going into alsamixer and "muting headphones" or something but there is just not an option for that for me.

my laptop is an advent 5401, i dont know much about the commands that can be done for the soundcard as im rather new to ubuntu.

im using ubuntu 9.10 if this helps.

help would be really appreciated as this is very annoying! thanks, dean.
Ahh pulseaudio strikes again. Go to system > admin > sound devices.

From there change everything to OSS or Alsa. If you change to alsa you will have to download the pulseaudio backend.

---

### Post by ghostcamera on 2010-01-05
when i go to system -> administrator    there is no link to sound devices

---

### Post by SecretCode on 2010-01-05
System > prefs > sound, various tabs, might be what he meant.

However I had this problem and there were no such different options in that utility. I found the solution by identifying my sound card as in this thread: [http://ubuntuforums.org/showthread.php?t=1075643](http://ubuntuforums.org/showthread.php?t=1075643) and editing alsa-base.conf as in this thread: [http://ubuntuforums.org/showthread.php?t=1075643](http://ubuntuforums.org/showthread.php?t=1075643)

---

### Post by ghostcamera on 2010-01-05
just checked the link u sent me

Codec: Realtek ALC268

thats what comes up in the terminal, so i checked mine against the list which was also on the link:

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)


what would my model number be? 
sorry for being a pain ^^

---

### Post by ghostcamera on 2010-01-05
bump, please this really needs sorting out :(

---

### Post by SecretCode on 2010-01-05
Unfortunately I think you just have to try each one in turn. Surprisingly, there doesn't seem to be a definite way to find this out.

---

