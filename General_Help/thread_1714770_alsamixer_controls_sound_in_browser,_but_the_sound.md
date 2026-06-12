---
title: "alsamixer controls sound in browser, but the sound indicator does not"
date: 2011-03-25
forum: General Help
---

### Post by ganeshsugunan on 2011-03-25
as the title says, alsamixer from the cl works fine for everything (sound is set to work through alsa, b/c autodetect doesn't work for some reason); but the regular sound indicator does not work for sound from within the browser (basically sound from flash, can't find a way to test if it's the browser, or the flash plugin that's the issue, though the issue does hold through both chrome and firefox) additionally, sound outside of the flash plugin (music files, etc) does not work at all. So it seems like the browser grabbed sound before the main controller, how do I deal with that on a regular basis?

ubuntu v. 10.04, gnome as window manager, alsa v. 1.0.22, card hda intel mid, chip realtek alc272 any more info you guys need?

---

### Post by ganeshsugunan on 2011-03-25
'alsactl init' fixed it btw (I don't think it's on a permanent basis, b/c of the nature of the issue (the problem does not always occur at boot) I can't be certain though.

---

