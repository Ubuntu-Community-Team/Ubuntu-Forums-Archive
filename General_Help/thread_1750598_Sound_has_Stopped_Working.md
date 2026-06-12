---
title: "Sound has Stopped Working"
date: 2011-05-05
forum: General Help
---

### Post by Spongejerk89 on 2011-05-05
I just installed Xubuntu on my old ThinkPad T40, and everything worked flawlessly until last night when I rebooted, and the sound stopped working. I'd rebooted it several times before with no problems.

Can anyone help?

---

### Post by 5149.5 on 2011-05-05
You would think that sound would be pretty easy. But it's not. I can understand problems caused by proprietary drivers but that's not usually the case with sound. Pulse audio should be flushed. It is overly complicated and difficult for a simple function like sound. I finally googled a blog that said exactly that. I uninstalled everything related to PA and got Alsa working. Unfortunately the rest of linux is devoid of sound support. At least I have sound for youtube, etc. Linux needs a little attention in the sound area.

---

### Post by Spongejerk89 on 2011-05-05
> **5149.5 said:**
> You would think that sound would be pretty easy. But it's not. I can understand problems caused by proprietary drivers but that's not usually the case with sound. Pulse audio should be flushed. It is overly complicated and difficult for a simple function like sound. I finally googled a blog that said exactly that. I uninstalled everything related to PA and got Alsa working. Unfortunately the rest of linux is devoid of sound support. At least I have sound for youtube, etc. Linux needs a little attention in the sound area.

So, can I assume that you don't know the answer to my problem?

---

### Post by Spongejerk89 on 2011-05-11
Sorry for the bump, but I really need help. I actually had a dream that I fixed the problem, then I woke up, and realized I didn't.

---

### Post by lidex on 2011-05-11
> **Spongejerk89 said:**
> Sorry for the bump, but I really need help. I actually had a dream that I fixed the problem, then I woke up, and realized I didn't.

That was me the other day - thought I was going to work - then the phone rang.
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Spongejerk89 on 2011-05-13
Didn't work :/

---

### Post by lidex on 2011-05-13
Try a suspend/resume cycle.

---

### Post by Spongejerk89 on 2011-05-14
*sigh*

That didn't work either.

---

### Post by 3 frags left on 2011-05-14
This happened to me once... I had to reinstall alsa all over again. You oughta try doing that.

---

### Post by lidex on 2011-05-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Spongejerk89 on 2011-05-15
It gave me [THIS]( http://www.alsa-project.org/db/?f=321419f8c77b2b59c926e3745b6c86d0d000ca9d).

---

### Post by lidex on 2011-05-15
Your PCM channels are muted - use alsamixer to unmute (the <M> key):
```
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
 [COLOR="Red"] Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off][/COLOR]
```

---

### Post by Spongejerk89 on 2011-05-16
I still can't figure this out, for whatever reason. Would you mind giving me instructions? Sorry for being a noob.

---

### Post by Spongejerk89 on 2011-05-16
Nevermind, I got it. Thanks so much for the help!

---

### Post by lidex on 2011-05-16
Long day here - you got it working?

---

### Post by Spongejerk89 on 2011-05-17
Yup, I have no idea how it got muted, but I fixed it. Thanks again.

---

