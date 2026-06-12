---
title: "beeping noise on shutdown of Ubuntu 9.04"
date: 2009-11-12
forum: General Help
---

### Post by Gatorade on 2009-11-12
can anyone tell me why it does this?

I installed Ubuntu 9.04 on a Dell laptop , but when shutting down the laptop it bleeps a couple of times at full volume.it does this even if I mute the volume.

---

### Post by t4thfavor on 2009-11-12
No idea, but I believe its the PC speaker being enumerated through your speakers. 

I usually blacklist the pcspkr module, and I know there is a place in alsamixer to mute just the pcspeaker device. Hope this gives you a place to start.

---

### Post by jollysnowman on 2009-11-12
You have to blacklist the pcspkr. For some reason in 9.04 it's enabled by default... and it was insaaanely loud on my laptop.

Add this to the end of /etc/modprobe.d/blacklist:

```
blacklist pcspkr
```

---

### Post by scouser73 on 2009-11-12
Follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown") to disable the shutdown beep.

---

### Post by Gatorade on 2009-11-12
> **jollysnowman said:**
> You have to blacklist the pcspkr. For some reason in 9.04 it's enabled by default... and it was insaaanely loud on my laptop.

Add this to the end of /etc/modprobe.d/blacklist:

```
blacklist pcspkr
```



what does this part mean exactly?
"Add this to the end of /etc/modprobe.d/blacklist:"

are you referring to opening up a terminal? and then just typing in blacklist pcspkr?

thanks for the replies, by the way.

---

### Post by Gatorade on 2009-11-12
> **scouser73 said:**
> Follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown") to disable the shutdown beep.

hey, thanks. just what I needed, I'll tell you if I got it to work.



thanks , worked perfectly.

---

