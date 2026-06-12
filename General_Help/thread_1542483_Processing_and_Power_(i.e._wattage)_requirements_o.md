---
title: "Processing and Power (i.e. wattage) requirements of software programs"
date: 2010-07-30
forum: General Help
---

### Post by noriek on 2010-07-30
Hi all,

This question could well apply to any computing environment but as I'm using Ubuntu (10.04) ....

I'm no power user but I recently installed a newer power supply, mostly for it's slightly better efficiency rating. It's the kind with multiple fan speeds and it increases cooling proportionally to the load being drawn.

So I've noticed, whilst using the standard "movie player" in full screen the power supply fan speeds up significantly, so much so that I need to increase the volume of whatever i'm watching. However, if I watch the same file in VLC no such fan speed up occurs. Now I realise this could be down to any number of encoding and decoding settings in each program but the quality of the output, on my fairly dated but still useable machine (P4 3.8 (from when clock speed mattered more than architecture!), and 1GB Ram), is equal to the human eye in both instances. Does this point to more efficient coding of software on VLCs part? Are there pieces of software out there which mean the same pc will use less power than if using similar software. If so, has such a list been compiled? I've not found one but I'd be interested in seeing one so my PC usage could be as green and responsive to use as possible.

Any ideas?

Cheers

---

### Post by Joe of loath on 2010-07-30
VLC uses way less CPU to play media files than gstreamer based programs like totem. My guess is you're drawing just enough extra power for the fan to speed up in totem, but not in VLC.

For anything that's not processor intensive though, it's all a level playing field really. Hardware is still way more important than the programs running on it (Except from the OS, on my hardware windows uses more power than Linux).

---

