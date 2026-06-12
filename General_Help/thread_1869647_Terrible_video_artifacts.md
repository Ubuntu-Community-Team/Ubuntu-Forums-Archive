---
title: "Terrible video artifacts"
date: 2011-10-26
forum: General Help
---

### Post by kerryhall on 2011-10-26
I don't know when this started, but it wasn't always like this. I've been getting pretty bad video artifacts. It sort of blurs the image at it plays for awhile, then every few seconds that blur will go away. Happens with pretty much every codec, although it is pretty noticable with flvs. I've been using vlc, but not sure if it is configured right. Mplayer causes a hard lockup every time I try to use it since enabling multi monitor support, but used to work great.

Thanks!

---

### Post by kerryhall on 2011-11-05
Bump

---

### Post by Man From Dirt on 2011-11-05
I've had luck with SMplayer in places were VLC wouldn't work and Mplayer just needed config. Could give that shot. It's in the repositories.

---

### Post by kerryhall on 2011-11-05
Thanks! What is SMplayer?

Are the decoders part of the media players themselves, or are they libraries that are used by all the media players?

I switched to vlc as mplayer causes a hard lockup on my system.

Maybe the decoder libraries aren't configured right?

---

### Post by Man From Dirt on 2011-11-05
It's a front-end to mplayer, and it has the configurations in the menus so it's easier to set up (imho).

---

### Post by kerryhall on 2011-11-06
Was gmplayer deprecated?

How do I configure the decoders to not have these artifacts?

---

### Post by Man From Dirt on 2011-11-06
> **kerryhall said:**
> Was gmplayer deprecated?

How do I configure the decoders to not have these artifacts?

I've never heard of gmplayer. In SMPlayer you can go to Video > Filters and Video > Deinterlace and play with those options. They're (what I assume) mplayer configs, just through a GUI. That's the best I'll be able to help you with bud. Good luck!

---

### Post by andrew.46 on 2011-11-08
> **kerryhall said:**
> Was gmplayer deprecated?

GMPlayer is still there and has even received a little development recently, but there are several other guis that are far superior.

---

