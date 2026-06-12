---
title: "Warcraft 3 Issue"
date: 2011-05-14
forum: General Help
---

### Post by UnknownDiety on 2011-05-14
I open it in fullscreen mode.

And if I go to desktop 2 (That way I can use Pidgin and Firefox) and then go back to desktop 1 it makes me have a window'd wc3 open. :(

How do I fix this?

Ubuntu 11.04

Didn't do this when I was using Ubuntu 10.10

---

### Post by enimeizoo on 2011-05-15
You can run a comand to have it fullscreen. Since you need to do it often, you could bind it to a key. 
```

wmctrl -r WindowName -toggle,fullscreen

```Not sure it works exactly the way you want, thought. I can't test since I don't have wine.
Good luck!

(edit) obviously, you want to replace WindowName by the actual name of the wc3 window. Part of it is enought, I'm not sure if it is case sensitive.

---

