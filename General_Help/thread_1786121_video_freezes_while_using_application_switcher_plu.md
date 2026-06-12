---
title: "video freezes while using application switcher plugin on ubuntu 11.04"
date: 2011-06-19
forum: General Help
---

### Post by ~!geek!~ on 2011-06-19
I am using ubuntu 11.04 with ati radeon 5470 (fglrx driver). The compiz fusion application switcher plugin causes the video to freeze. Although sound does not stop.
 Once you select the window playing video, the frozen video plays normally.
Any solutions...

---

### Post by ~!geek!~ on 2011-06-19
It seems only I am having this trouble with compiz. Some replies guys...

---

### Post by ~!geek!~ on 2011-09-17
> **~!geek!~ said:**
> I am using ubuntu 11.04 with ati radeon 5470 (fglrx driver). The compiz fusion application switcher plugin causes the video to freeze. Although sound does not stop.
 Once you select the window playing video, the frozen video plays normally.
Any solutions...

  Okay so finally solved this myself!!!  If anyone else's facing this, Here is the solution!  The problem was with `MipMaps` option selected in switcher plugin! It seems Ubuntu 11.04's underdeveloped unity thing does not go along with the gpu mentioned in the original post well! Once you deselect the Mipmaps option, the problem is solved. (BTW, Mipmap option lets your machine do high quality scaling of images while switching windows). I could not find much difference with or without this option, but it solved my problem!  I hope it's been already solved in ubuntu 11.10's gnome 3.0! Anyhow marking this thread solved now!!

---

