---
title: "Sound Issue and Question"
date: 2006-06-17
forum: General Help
---

### Post by Cable on 2006-06-17
**Sound Issue:  **I have 5.1 speakers and like listening to music using all of them.  Every time I restart/boot my computer, I have to turn the "Surround", "Center", and "LFE" volumes back up so that the rear, center, and subwoofer speakers actually get used.  They are always turned all the way down.  Is there any way to make it so they just stay where I set them even after restarting/booting?

**Sound Question:  **I like to listen to my music at higher volumes than I like other applications to be at (for obvious reasons).  Is there some way to give a volume boost to my music player so I can keep it at the desired volume but other applications aren't so loud when they make sounds?

---

### Post by christhemonkey on 2006-06-17
For the sound issue,

Try setting things to where you want;
And then type into a terminal:
```
sudo alsactl store 
```

As for the sound question, i have no idea....
You could probably do some crazy scripting magic... but as i said, have no idea!

---

