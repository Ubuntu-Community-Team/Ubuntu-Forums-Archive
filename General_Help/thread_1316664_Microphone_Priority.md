---
title: "Microphone Priority?"
date: 2009-11-06
forum: General Help
---

### Post by G226 on 2009-11-06
Is there any way to set a USB microphone when upon being plugged in it will become the default input/microphone?

As it is now the default device is the internal soundcard of the laptop, everytime I want to use a USB microphone, I have to set it as the active input after plugging it in or turning the laptop on.

Thanks!

Using Ubuntu 9.10.

---

### Post by P4man on 2009-11-06
Yep its possible.
Install 
```

sudo apt-get install pavucontrol
```

then open it from apps > sound > pulseaudio volume control

 Open your recording or IM app, start recording and assign the recording stream to your USB mic in "recording"
On the input tab you can define a fallback device. Set the internal one as fallback.

im no expert and I find the screen pretty confusing (very hard to see if you clicked the fallback option or not) but it works fine here.

---

### Post by P4man on 2009-11-06
actually..scratch that. its still reverting to onboard audio by default after unplugging and replugging my usb headset.

I guess Im in the same boat as you

---

### Post by G226 on 2009-11-06
Yes, I tried what you said before you posted the second time, it didn't work for me either :(

---

### Post by G226 on 2009-11-06
Darn, no one knows? I've tried google and the Ubuntu IRC channel in freenode.

---

### Post by leeds_shrew on 2010-03-27
Did this issue ever get solved? I too have a USB headset and I'd like it to be switched to automatically when I plug it in - useful for answering unexpected Skype calls in a hurry!

Cheers,

G

---

