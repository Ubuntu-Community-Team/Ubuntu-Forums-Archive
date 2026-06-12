---
title: "ffmpeg video filters in lucid"
date: 2011-10-10
forum: General Help
---

### Post by J V on 2011-10-10
Where are they?...

I've installed medibuntu, lucid-bleed, nothing has video filters, none of them even respond it's like: "Unrecognized option 'vf'"

Geeze even debian has a working ffmpeg in the default repos...

---

### Post by FakeOutdoorsman on 2011-10-10
You can compile FFmpeg to get filter support: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You can then see your available filters with:
```
ffmpeg -filters
```

---

### Post by J V on 2011-10-10
It's 2011! Why do I have to compile anything at all?

If necessary, can't I just install the debian repositories and go from there?

How would I set it not to use that repo unless a package is specifically set to that version?

---

