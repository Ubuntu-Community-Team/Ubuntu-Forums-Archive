---
title: "How do I turn off sound effects?"
date: 2012-06-14
forum: General Help
---

### Post by okok on 2012-06-14
I don't know whether this is a problem in my computer or a general bug, but my Sound Effects tab under Sound Settings contains only a list of alert sounds and an alert volume, which is on 'Off', but this makes no difference: I keep hearing those annoying effects.

Is there a way to get rid of them beside deleting the sound files that contain them?

What makes me suspect that there might be a specific problem in my computer is that under the speaker testing dialog (in the Hardware tab of Sound Settings) makes no sound, although sounds from all applications (and, sadly, also the annoying built-in sound effects) are heard.

---

### Post by okok on 2012-06-16
Really nobody knows how to turn off the sound effects in Ubuntu 12.04?

---

### Post by wtetzner on 2012-06-16
> **okok said:**
> Really nobody knows how to turn off the sound effects in Ubuntu 12.04?
Open System Settings, click on "Sound", then the "Sound Effects" tab.

Click the "off" switch for "Alert volume".

---

### Post by okok on 2012-06-16
Thanks, that's the obvious thing to do, but as I explained above, this has no effect.

> **wtetzner said:**
> Open System Settings, click on "Sound", then the "Sound Effects" tab.

Click the "off" switch for "Alert volume".

---

### Post by wheeze on 2012-06-16
Can't offer a solution, sadly, but I can say that this same thing happens on my computer as well so I don't think it's a problem with your machine.

I'll be watching this in hope of an answer as well!

---

### Post by Jeff250 on 2012-07-18
This is what I figured out for turning off the alert sounds in 12.04:

Open dconf-editor.  Browse to
org/gnome/desktop/sound
On the right, unclick event-sounds.

The alert sounds should then be disabled.  I don't know if this also disables other sounds other than alert, but if it does, they're likely sounds that I would want disabled anyways.

---

### Post by okok on 2012-07-19
I was eventually able to get rid of those annoyances using [Ubuntu Tweak]("http://ubuntu-tweak.com/"). Under the 'Sound' section there is a selector for Event Sounds, and unlike the one in Ubuntu's own Sound Settings, this one does work.

---

