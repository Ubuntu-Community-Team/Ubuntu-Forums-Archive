---
title: "Help closing these 3 window bars."
date: 2010-05-20
forum: General Help
---

### Post by mnicholson1618 on 2010-05-20
So I have these three bars that I suppose are some kind of left over fragment of windows I had up the last time I rebooted. Anyhow, whenever I boot now, these three bars show on my desktop, and I cant get rid of them, they dont have the minimize, maximize or close buttons. Yet when I click the, "show desktop" buttom, they then minimize. HOwever, they don't show up on my window list. I've tried restarting my xsession and that didnt work, I've restarted nautilus that didn't work, I cant right click on them, I already tried xkill and force quite and that doesnt work. They're just always there. PLz help...

---

### Post by dino99 on 2010-05-20
try:

metacity --replace
sudo dpkg --configure -a

are you using some "exotic" repo and packages like theme(s) (try with an other theme to see the difference)

---

### Post by mnicholson1618 on 2010-05-27
ACtually, I figured it out, I guess the first time I restarted my x session I didnt do it right, because when I tried it again it totally worked, but thanks for the post, this was my first thread.
And just fyi, I think I had tried that metacity --replace, that hadn't worked, and I also remember trying different themes, not that the ones I was using where too exotic, just some regular gtk+2.x ones I picked up from gnome-look. But again, thanks!

---

