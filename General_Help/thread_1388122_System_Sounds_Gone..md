---
title: "System Sounds Gone."
date: 2010-01-22
forum: General Help
---

### Post by chrispche on 2010-01-22
My system sounds have gone since doing an upgrade. Anyone else notice this?

---

### Post by Enigmapond on 2010-01-22
By "system sounds" do you mean all sound?

---

### Post by n0dix on 2010-01-22
Try this:
```
rm -rf ~/.pulse
killall pulseaudio
```

Also see this thread: [http://ubuntuforums.org/showthread.php?t=1308550](http://ubuntuforums.org/showthread.php?t=1308550)

---

### Post by chrispche on 2010-01-23
What will that code do?

---

### Post by fjf314 on 2010-01-23
It looks like it deletes the contents of the folder with the user configuration information for pulse in your home directory and then kills the process for it.

---

### Post by jbruced on 2010-01-23
Maybe try qamix(load from synaptic), and turn all controls up and/or unmute anything set.

Easy to try.

Hope it helps.

GL
Bruce

---

### Post by n0dix on 2010-01-23
> **chrispche said:**
> What will that code do?

Delete the user 'pulse' configuration and kill the process of pulseaudio.

---

### Post by llawwehttam on 2010-01-23
This should work. It makes the audio process re-configure itself when you next log-in.

---

### Post by chrispche on 2010-01-23
> **n0dix said:**
> Try this:
```
rm -rf ~/.pulse
killall pulseaudio
```

Also see this thread: [http://ubuntuforums.org/showthread.php?t=1308550](http://ubuntuforums.org/showthread.php?t=1308550)

This has worked thanks.

---

### Post by n0dix on 2010-01-23
Don't forget the SOLVED tag.

---

