---
title: "can't turn off sounds"
date: 2011-01-18
forum: General Help
---

### Post by frabato56 on 2011-01-18
Hi All,

I just installed ubuntu studio and it looks better than ever. I have an ice1712 soundcard and I have NEVER had it work on ANY linux distribution that used pulseaudio (I'm guessing that this problem has been around for at least two years) so I proceeded with my usual way of fixing things which is to just get rid of pulseaudio. Well it worked like a charm, uninstall pulseaudio, reboot and there's my sound. Here is my problem, I went to >system >preferences >sound to turn of the system sounds. I get a message, "waiting for sound system to respond" Does anyone know how I can make these sounds go away. I'm happy to try anything.

Thanks!

---

### Post by Old_Grey_Wolf on 2011-01-18
If you are talking about the login sound, you can enter this into the terminal ```
gksudo nautilus /usr/share/sounds/ubuntu/stereo
```and rename the desktop-login.ogg file to something else. There are other sound files there as well; such as, the desktop-logout.ogg file. This should work for the Ubuntu Studio version.

---

### Post by frabato56 on 2011-01-18
Thanks for the reply, I wasn't referring the login sounds although I'd like to turn them off too. I'm talking about the clicks that happen anytime I open a program.

---

### Post by Old_Grey_Wolf on 2011-01-18
I don't get those sounds; however, the sound file is probably in one of the other folders within "/usr/share/sounds". I use a plain Ubuntu 10.04 install that may not have those sounds enabled. Try looking around in the other "/usr/share/sounds" directories. When I hover the cursor over a file I hear the sound it makes.

Maybe someone will come along to help you install an alternative application for pulseaudio. That is probably the best solution.

---

### Post by frabato56 on 2011-01-18
Thanks Old Gray Wolf, It was easy, I just threw all of the sounds in the trash and now it behaves just the way I want it to.

---

### Post by Old_Grey_Wolf on 2011-01-18
> **frabato56 said:**
> Thanks Old Gray Wolf, It was easy, I just threw all of the sounds in the trash and now it behaves just the way I want it to.

I hope it works out for you in the long term. :)

---

