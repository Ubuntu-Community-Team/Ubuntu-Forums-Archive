---
title: "Difference between X org and Xfree86"
date: 2005-03-16
forum: General Help
---

### Post by lao_V on 2005-03-16
Hi,

Can anyone tell me what differentiates xorg from xfree86? And what are the pro's/con's of both?

Thanks!

---

### Post by ssam on 2005-03-16
The story is:
first there was xfree, a few people were not happy with the way its code was structured, and it slow pace of developement. There were atempts to change or fork it, but they could never get the momentum they needed. Then xfree made a licence change, that some distributions felt was not good (i am not sure exactly what it was). very quickly the xorg fork was created. it was basically a copy of the last version before the licence change. the xorg branch is developed far more openly and so has made some big steps in the past year or so. new modules have been added, to improve things like redrawing and transparency. most of the linux distributions have switch to xorg.

at the moment there is not a huge amount of difference between the two, but as xfree developement has slowed/stopped you will probably want to change at some point. it probably best to stick with what the distibution is shipping. warty was xfree, hoary will be xorg.

---

### Post by jallen7usa on 2005-03-17
I too have been curious about this for a while so thanks for that reply.

Instead of creating a new thread on the subject I'll ask my question here.  I've been running Warty for a few weeks now and after some trials and tribulations (linux newbie) I was able to get dual monitors working via XFree.  I've been thinking about doing a dist-upgrade to Hoary but I'm worried about my displays working.  Can I use my config file from XFree or will I have to re-create a new config file in some new format.

---

### Post by c_dog on 2005-03-18
Nope, you shouldn't have to changed the file, XF86Config is for now compatible with Xorg. Some distributions like SuSE even haven't got around to changing their config tools from XF86Free even though they use Xorg now. They just symlink the xorg.conf to XF86Config.

---

