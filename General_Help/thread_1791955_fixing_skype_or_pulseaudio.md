---
title: "fixing skype or pulseaudio"
date: 2011-06-27
forum: General Help
---

### Post by enimeizoo on 2011-06-27
Hello,
I can't have skype detect my mic. Actually, pulseaudio doesn't seem to be aware of it. I can set its volume with alsamixer, but if I want to record it (with audacity for example), it won't work unless I choose "HDA intel :connexant analog". Other choices are default or pulse.

In skype, I don't have a choice, it wants pulseaudio as the audio input. 

How do I get pulseaudio to find my mic?

Thanks.

---

### Post by enimeizoo on 2011-06-28
fixed...
sudo apt-get autoremove pulseaudio

Sound never worked that well... Won't even try to understand.
Both skype and audacity behave just like it should.

---

