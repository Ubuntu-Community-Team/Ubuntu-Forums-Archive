---
title: "pulseaudio null output"
date: 2009-07-31
forum: General Help
---

### Post by shlteater on 2009-07-31
after an update to kernel 2.6.28-13-generic ,
I've got no sound in my ubuntu now.
and the device in my volumn control shows
Playback: Null Output(Pulseaudio Mixer)

my sound card here
```
shlteater@shlteater-laptop:/proc/asound$ lspci | grep HD
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

but vi /proc/asound/cards got the file just
--- no soundcards ---

does it mean that my system failed to load it?

---

### Post by emid on 2009-08-02
I have the same issue on 2.6.28-14-generic.

---

### Post by emid on 2009-08-07
bump.... having no audio kinda sucks

---

### Post by peterthebike on 2009-10-02
Did you two ever get a fix?

I have just updated 2.6.28-15.49 to 2.6.28-15.52 and I have now got null output on pulseaudio.

---

