---
title: "fluxbox wont load background on start up!"
date: 2006-03-18
forum: General Help
---

### Post by jinxjinx on 2006-03-18
Hi, my fluxbox start up file looks like this:


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.
fbsetbg .fluxbox/backgrounds/bg.jpg
aterm &
gkrellm &
gnome-volume-manager &
xscreensaver -nosplash &

with all else comments.

everything else loads, but for some reason fluxbox cant load the background. And if i try it with fbstebg -l it tells me there is no previously set background, but there was one!

help
thanks

---

### Post by taurus on 2006-03-18
[QUOTE=jinxjinx]Hi, my fluxbox start up file looks like this:


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.
fbsetbg .fluxbox/backgrounds/bg.jpg
aterm &
gkrellm &
gnome-volume-manager &
xscreensaver -nosplash &

with all else comments.

everything else loads, but for some reason fluxbox cant load the background. And if i try it with fbstebg -l it tells me there is no previously set background, but there was one!

help
thanks[/QUOTE]

It should be
```

fbsetbg -f /home/username/.fluxbox/backgrounds/bg.jpg

```

---

