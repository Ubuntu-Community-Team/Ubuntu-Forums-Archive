---
title: "Pulseaudio terminal commands to change song"
date: 2012-09-08
forum: General Help
---

### Post by BlackoutWorm on 2012-09-08
Hello. I use ubuntu studio with pulse instead of alsa.
So I'd like to know what the pulseaudio commands for next and previous tracks are?
In gnome there are keyboard shortucts for this already, but for some weird reason, the keyboard shortcut app doesn't tell you what the commands are.

So do any of you guys know what these commands are for next and previous played track.

---

### Post by cryptotheslow on 2012-09-08
Do you mean using Alt+Right and Alt+Left?

If so those are Rhythmbox shortcuts.

PulseAudio is just a sound server and as far as I know has no control over the application generating the sound.

If you are using Rhythmbox you can use these commands to achieve what you want:

rhythmbox-client --next
rhythmbox-client --previous

There's plenty of other things you can do with rhythmbox-client - use the command "man rhythmbox-client" to review them.

---

### Post by BlackoutWorm on 2012-09-08
Thanks a lot, I didn't know that.
But that isn't actually what I mean.
You know in gnome there's a keyboard shortcut software thing where you can add keybindings for everything?
There's already one there for next and previous song. I think it uses the volume applet.
Does anyone know what the commands for that?

---

### Post by BlackoutWorm on 2012-09-10
**[color="blue"]bump[/color]**

---

