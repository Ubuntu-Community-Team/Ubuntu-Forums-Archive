---
title: "IVTV driver - MythTV is only choice?"
date: 2006-04-24
forum: General Help
---

### Post by Vermyndax on 2006-04-24
Hi there...

I'm wondering... if I'm using an IVTV card (PVR-150) - is MythTV really my only choice for a tv app to view?  I'd *like* to have something that can sit in the corner (like tvtime, but that doesn't work with ivtv).  Anyone have any ingenius setups with ivtv cards?  Any cron scripts to do recording or anything?

Can you tell I'm trying to avoid MythTV and all of the overhead that comes with it?

---

### Post by paulprovost on 2006-04-24
mplayer plays ivtv video. Try

```
mplayer /dev/video0
```

You'll have to use ivtv-tune to change channels.

---

### Post by dlai on 2006-05-01
yeah...does anybody know if there is an application out there that can "do it all" for the ivtv-based cards aka. mpeg2 encoded cards. It's too much of a hassle running mythtv everytime...

---

### Post by dlai on 2006-05-15
well actually I found out that the new xawtv 4.0 is doing the ivtv drivers.... look at this thread.[http://www.ubuntuforums.org/showthread.php?t=17088]("http://www.ubuntuforums.org/showthread.php?t=17088")

---

