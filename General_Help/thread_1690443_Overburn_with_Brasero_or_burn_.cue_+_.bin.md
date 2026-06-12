---
title: "Overburn with Brasero or burn .cue + .bin"
date: 2011-02-18
forum: General Help
---

### Post by Asmodai on 2011-02-18
Hey,

I need to burn tracks that total to 80-82 minutes on 80min CDs.
However, Brasero stops the burning process right at the start complaining there is not enough space on the CD. I tried having Brasero create an image and burn it with k3b. However, Brasero creates a .cue and a .bin file, but when loading the .cue file, k3b says that it does not seem to be a valid image, even when selecting ".cue/.bin image" or "audio cue file" as the image type. k3b itself refuses to burn .mp3 files without manual conversion.

So... what should I do to achieve my goal?

---

### Post by Asmodai on 2011-02-18
I also tried to convert the .cue and .bin file to .iso using bchunk.
Which creates a .cdr file for every single track on the CD, which k3b apparently does not recognize as anything that you could possibly burn on an audio CD.

---

### Post by Asmodai on 2011-02-18
Bump. This is urgent.

---

### Post by Asmodai on 2011-02-19
I have access to a Windows machine, so I also tried CDBurnerXP (overburning option is grayed out), Nero BurnLite (does not support burning audio CDs at all) and Ashampoo Burning Studio (does not support overburning).
Something so trivial can't possibly be this hard to do...

---

### Post by Asmodai on 2011-02-19
I converted the mp3 tracks to wave format using:
```
for i in *.mp3; do mpg321 -w "`basename "$i" .mp3`.wav" "$i"; done
```While manual conversion is not an acceptable solution, I could now successfully burn the CDs with k3b.

---

