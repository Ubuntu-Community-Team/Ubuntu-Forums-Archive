---
title: "freaky Mplayer error"
date: 2006-05-24
forum: General Help
---

### Post by threethirty on 2006-05-24
the error reads like this
```
New_Face failed. Maybe the
font path is wrong.
Please supply the text font file
(~/.mplayer/subfont.ttf).
```

and I can't seem to find the above mentioned file](*,)

---

### Post by adamkane on 2006-05-24
Install mplayer according to the CVS Mplayer Howto, or just install gxine (xine-ui) to play your media:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28xine-ui.29)

---

### Post by threethirty on 2006-05-24
i wasnt really looking to reinstall it. It plays fine, but it just wont go full screen or get any bigger than it starts at

---

### Post by adamkane on 2006-05-25
Still gotta use the howto:
[http://www.ubuntuforums.org/showthread.php?t=85190](http://www.ubuntuforums.org/showthread.php?t=85190)

---

### Post by nalmeth on 2006-05-25
Change the video driver in preferences, will give you different fullscreen behavior.
I know that there's a quickfix for that font problem, only can't remember what. A lot of people have seen it.
Will post if I find it.

---

### Post by threethirty on 2006-05-25
if i set gxine (xine-ui) to assoc. with my media files will it screw up the firefox mplayer plug-in or will it work embedded in firefox?

---

### Post by nalmeth on 2006-05-25
You mean just for files on your harddrive? No that won't screw up the mplayer-mozilla behavior.

---

### Post by threethirty on 2006-05-25
Sweet thanks, alls well now

---

### Post by ice60 on 2006-05-25
[QUOTE=threethirty]the error reads like this
```
New_Face failed. Maybe the
font path is wrong.
Please supply the text font file
(~/.mplayer/subfont.ttf).
```

and I can't seem to find the above mentioned file](*,)[/QUOTE]
hi, you can fix that error by installing mplayer-fonts
```
sudo apt-get install mplayer-fonts
```

---

### Post by adamkane on 2006-05-25
gxine (xine-ui) will probably be replaced as your embedded media player. It plays more stuff, so it's probably a good alternative.

---

### Post by EmmEff on 2006-05-25
[QUOTE=threethirty]i wasnt really looking to reinstall it. It plays fine, but it just wont go full screen or get any bigger than it starts at[/QUOTE]

Also, FWIW, the error you're seeing has nothing to do with either of those problems you have described.  The error is simply indicating that the subtitle font is missing.

---

