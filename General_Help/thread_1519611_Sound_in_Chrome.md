---
title: "Sound in Chrome?"
date: 2010-06-28
forum: General Help
---

### Post by willchurch on 2010-06-28
Whenever there is sound played in Chrome (i.e. youtube, etc.) the sound does not play. If it is a video playing, the visual part works, but again, no sound. Could it be something to do with flash? Sound works fine in Firefox, and in other applications, just not Chrome.

---

### Post by renkinjutsu on 2010-06-28
Pulseaudio can control the output of individual applications. Make sure pulseaudio isn't muting Chrome. Or maybe Chrome isn't even using Pulseaudio

---

### Post by willchurch on 2010-06-28
How do I do that?:confused:

---

### Post by renkinjutsu on 2010-06-29
right click on the volume icon on your panel and click sound preferences (Or go to a terminal and type gnome-volume-control ), then click the "Applications" tab while chrome is open

---

### Post by willchurch on 2010-06-29
Thanks renkinjutsu, it was indeed muted.

---

