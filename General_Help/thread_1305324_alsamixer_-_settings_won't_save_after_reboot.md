---
title: "alsamixer - settings won't save after reboot"
date: 2009-10-29
forum: General Help
---

### Post by acer8930 on 2009-10-29
Hello,

I'm on Ubuntu 9.10 Karmic Koala.

My laptop has a 5.1 surround sound, and my Center speaker is blown (crackles when playing) so I need to disable it.

I "**sudo alsamixer**"
Lower the center speaker to "**00**".
Hit "**ESC**"
"**sudo alsactl store**" to save settings.
When I reboot, the Center speaker is back to normal and I need to repeat the process.

I've seen some forums say to use "**amixer**" but I can't figure it out.
Anyone know how I can solve this problem?

---

### Post by mCion on 2009-11-03
similar problem here, need to mute the external speaker or else I have no sound.  I've also tried following those instructions to save alsamixer settings with no success.

ideas anyone?

---

### Post by P4man on 2009-11-03
you dont need sudo to run alsamixer. In fact perhaps thats even your problem. Try setting alsamixer without sudo.

If that fails try

```
amixer set 'PCM Center',0 0
```

If that works, add it to your session.

---

### Post by whitethorn on 2009-11-03
Hi I had something of the same problem with the beta.  Here's a fix that works for me.

[http://ubuntuforums.org/showthread.php?t=1290130](http://ubuntuforums.org/showthread.php?t=1290130)

I'm not sure if you need sudo alsamixer.  I can't even use the volume button on my keyboard because as soon as I touch it my PCM volume goes full and it sounds like s***.

---

### Post by acer8930 on 2009-11-03
> **P4man said:**
> you dont need sudo to run alsamixer. In fact perhaps thats even your problem. Try setting alsamixer without sudo.

If that fails try

```
amixer set 'PCM Center',0 0
```

If that works, add it to your session.

That works, but I needed to remove "PCM":

```
amixer set 'Center',0 0
```

Works perfectly now.
Thanks for the help.

---

