---
title: "No sound anywhere!"
date: 2010-03-02
forum: General Help
---

### Post by Sugoi48 on 2010-03-02
I have no sound. None on the example content (Aesop's Fables), none on Youtube, none anywhere. The main volume settings are up and the app-specific volumes are up. I tried with headphones too. And yes my speakers work! :P Any ideas? Thank you!

---

### Post by srix on 2010-03-02
Firstly, have you tried the alert sounds in the Sound Preferences to see if those play? 

Secondly, please post some details about your system:

What system do you have? Desktop/laptop? Which version of Ubuntu? Any idea which sound card is installed? If not, run the command "lspci" in a terminal and look for a line that has "Audio" in it. Also, run this command in a terminal and post the output here:
cat /proc/asound/card0/codec#0 |grep Codec

---

### Post by Sugoi48 on 2010-03-02
I tried the alert sounds with no luck. I'm on a high-end MacBook Pro (new as of September '09). Thank you! Results as follows:
Codec: Generic 1013 ID 4206

---

### Post by Lightstar on 2010-03-02
type alsamixer in terminal
see if your volumes are up in there too

---

### Post by srix on 2010-03-02
Try adding this line to the end of your /etc/modprobe.d/alsa-base.conf:
options snd_hda_intel model=mbp3

and reboot.

And as Lightstart said, also check that the volumes are raised high in alsamixer.

---

### Post by Sugoi48 on 2010-03-02
"Try adding this line to the end of your /etc/modprobe.d/alsa-base.conf:
options snd_hda_intel model=mbp3"
How do you do that?
alsa-mixer in terminal had the volume up.

---

### Post by Nordite on 2010-03-02
What version of Ubuntu are you using?
Nordite

---

### Post by Sugoi48 on 2010-03-02
I'm on 9.10 Karmic Koala.

---

### Post by Clancy_s on 2010-03-02
> **Sugoi48 said:**
> > "Try adding this line to the end of your /etc/modprobe.d/alsa-base.conf:
options snd_hda_intel model=mbp3"
How do you do that?
alsa-mixer in terminal had the volume up.

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

put in your password, add the line, save and exit.

You might want to make a back up copy somewhere first, although it's a fairly minor change and would be easy to undo.

---

### Post by lyall on 2010-03-02
check your sound setting
System > Preferences > Sound

On the sound Effects tab
first check to see if Mute is checked
Second check the Alert volume
Third check the Hardware tab to see which device you are using
Fourth check the Profile:
if you are going to use you Microphone 
check and see if is Muted

Fifth check the Output tab
check you Balance
last check your Connector

good luck and have fun learning

---

### Post by Sugoi48 on 2010-03-02
...

---

### Post by Sugoi48 on 2010-03-02
I've done those first five things. Could you clarify the connector one? I tried this with headphones too, if that helps. Thanks

---

