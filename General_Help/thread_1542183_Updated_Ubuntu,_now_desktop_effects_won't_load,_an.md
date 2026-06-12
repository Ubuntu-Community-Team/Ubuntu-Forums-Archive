---
title: "Updated Ubuntu, now desktop effects won't load, and cairo dock has a black box"
date: 2010-07-30
forum: General Help
---

### Post by kuraykillua on 2010-07-30
So I just updated Ubuntu, restarted, and now desktop effects isn't working and cairo dock has a big black box behind it.
From what I've found, I need to update my graphics card (nVidia)driver every time I update. I used hardware manager, clicked remove, and then activate again, restarted my computer but it's still the same.
I've also read something about nvidia-xconfig, and restart X. Since I'm still relatively new to linux, I'm not sure what that is.
I'm pretty sure I need to update my driver using another method, but I'm not sure what that is.

---

### Post by stoneage on 2010-07-30
If you use the proprietary driver you will have to recompile the module every time there is a kernel update.

---

### Post by kuraykillua on 2010-07-30
Ah ok. How do I do that?

---

### Post by kuraykillua on 2010-07-30
Oh man the solution was really easy. Enable extra visual effects under appearance. I can't believe I've spent hours just to figure out how to do that...
Apparently updating ubuntu resets that option. I did not know that.

---

