---
title: "d4x shuts down by itself constantly !!!"
date: 2006-02-17
forum: General Help
---

### Post by Mishal on 2006-02-17
WHY ON EARTH is this HAPPENING? I am going nuts:confused: :cry: 

d4x insists on closing by itself after running for 1 minute. Have I been hacked or something? Or is there some remote proceduce call on Linux that commands some program to be shut down?:confused:

---

### Post by Mishal on 2006-02-17
Okay, I have run d4x in the terminal...it says 'segmentation fault'. Help!

---

### Post by jrib on 2006-02-17
use the default gnome theme and see if it still happens (human is default I think, but I know it works with clearlooks since that's what I use).  I remember some themes caused some prolems with d4x

---

### Post by Mishal on 2006-02-18
Thanks but I found out the problem. It was with a particular file being downloaded in d4x that was causing it. I removed it and it was all fine again. But WHY the file was acting so peculiarly...I don't know!

---

### Post by LacteuS on 2006-06-09
Well, I've this segmentation fault too. I never used it before :'(


% d4x

(d4x:6249): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:6249): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:6249): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:6249): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:6249): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:6249): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
zsh: segmentation fault  d4x

---

