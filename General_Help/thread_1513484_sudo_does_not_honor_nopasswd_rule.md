---
title: "sudo does not honor nopasswd rule"
date: 2010-06-19
forum: General Help
---

### Post by Jordanwb on 2010-06-19
I've got Openbox working fairly well. I add the following line to the beginning of /etc/sudoers:

```
jordanwb ALL=(ALL) NOPASSWD: /sbin/shutdown, /sbin/halt, /sbin/reboot
```

I issue "sudo reboot", sudo still asks me for my password. I'm trying to run "sudo reboot" through a key binding. Any ideas?

---

### Post by kerry_s on 2010-06-19
don't put spaces after the ","

jordanwb ALL=(ALL) NOPASSWD:
should be
jordanwb ALL=NOPASSWD:

here's what mine looks like, i seperate for easy management, but it can all be on 1 line.

---

### Post by Jordanwb on 2010-06-19
That was it. Thanks. now I got to get pulseaudio working.

---

### Post by sisco311 on 2010-06-19
never mind

---

### Post by kerry_s on 2010-06-19
> **Jordanwb said:**
> That was it. Thanks. now I got to get pulseaudio working.

don't forget to add "start-pulseaudio-x11 &" to your autostart.

---

### Post by Jordanwb on 2010-06-19
> **kerry_s said:**
> don't forget to add "start-pulseaudio-x11 &" to your autostart.

I added my user to the audio group and I can change the defaut output just fine through the gnome-volume-control-applet.

[Edit]

Hold on a second. Sudo isn't working right.

```
jordanwb ALL=NOPASSWD: /sbin/shutdown,/sbin/halt,/sbin/reboot
```

It's still asking for my password.

---

### Post by sisco311 on 2010-06-20
> **Jordanwb said:**
> 
[Edit]

Hold on a second. Sudo isn't working right.

```
jordanwb ALL=NOPASSWD: /sbin/shutdown,/sbin/halt,/sbin/reboot
```

It's still asking for my password.

*sudo reads the sudoers file and applies permissions in order from top to bottom. So the last line in the file will overwrite any previous conflict with the config settings. **So it is best to put new configuration lines at the bottom**.*

```
jordanwb ALL=(ALL)NOPASSWD:/sbin/shutdown,/sbin/halt,/sbin/reboot
```

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

