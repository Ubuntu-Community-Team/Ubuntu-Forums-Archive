---
title: "Sound stopped working in Flash in Firefox"
date: 2009-08-16
forum: General Help
---

### Post by balloonatic on 2009-08-16
Hi all,

The sound in my flashplayer has completely gone, sound works fine on other players but when I try to play, for example, a youtube video, its totally silent.

It's worked fine for ages, not sure if it was a FF update or something I did. All I can think of is that I installed "ear candy" (which didn't work) and have now disabled it, I also installed chromium and the closest I came to FF then was when I did the command

```
cd /usr/lib/chromium-browser/plugins
sudo ln -s usr/lib/flashplugin-installer/libflashplayer.so
```

to enable flash in chromium. I got sick of chromium pretty quickly and went back to FF which then had no sound in flash vids. It's probably that or the earcandy thing thats broken it but I cant see how.

Any help much appreciated :)

---

### Post by balloonatic on 2009-08-18
BTW, sound works fine in Chromium flash player, which is the most puzzling part.

---

### Post by Tamalin on 2009-08-18
Are you running another OS in a virtual machine while you try and play sounds.  When a VM like VirtualBox is used, the sound can be captured so that sound will only come from sources inside the guest OS.  Anything played outside would be silent.

---

