---
title: "Speaker burp on system Shutdown"
date: 2009-12-01
forum: General Help
---

### Post by sccrstvn93 on 2009-12-01
I ma running ubuntu 9.10 and occasionally experience a speaker "burp" when I shutdown my computer. My computer emits a loud buzzing sound as if the speakers are discharging. The sound may also be a system beep. I am using a dell studio xps 16. I have disabled pcspkr and all system beeps. Thanks for the help. Any ideas on how to fix this?

---

### Post by sccrstvn93 on 2009-12-02
bump

---

### Post by Iowan on 2009-12-02
My Jaunty laptop has similar sound (I call it a "scratch") when it shuts down.  I'm happy enough that I got sound working that I'm not too sure I want to fix the problem - if fix is total silence... again.

---

### Post by sccrstvn93 on 2009-12-03
Does anyone know if this is dangerous for my speakers?

---

### Post by sccrstvn93 on 2009-12-05
bump

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
I get a pop whenever something accesses the sound card and whenever I shutdown/boot. If it's not reeeaaally loud then I don't think it will do anything to the speakers. If it is then make sure you turn down/off the volume when you shut down.

---

### Post by sccrstvn93 on 2009-12-05
The setting of the volume has no effect on the volume of the buzzing sound.

---

### Post by wojox on 2009-12-05
Tried this:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

changing the line

```
options snd-hda-intel power_save=10 power_save_controller=N
```

to read

```
options snd-hda-intel power_save=0 power_save_controller=N
```

Reboot.

---

### Post by sccrstvn93 on 2009-12-05
Thanks for the suggestion, but the buzzing still happens on shutdown and restart.

---

### Post by sccrstvn93 on 2009-12-07
bump

---

