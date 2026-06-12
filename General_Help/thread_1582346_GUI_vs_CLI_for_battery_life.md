---
title: "GUI vs CLI for battery life"
date: 2010-09-26
forum: General Help
---

### Post by JohnElway on 2010-09-26
I was disappointed to learn that Linux typically doesn't get the kind of battery life that Windows does, so I've been researching ways to remedy this (i.e. using power management tools like powertop). On my netbook, I don't do much other than light web browsing and word processing (which I usually do in a text editor anyway), so would it make sense to save battery life by doing all this in CLI mode? For example, as soon as the desktop loads I could stop X server at a terminal:

```
sudo service gdm stop
```

switch to a terminal using CTRL+ALT+F1-6, and use Lynx/Vim to do everything. Do you guys think this would actually save battery power compared to just running X like I normally do? Also, would using only the CLI in Ubuntu give it comparable battery life to Windows 7?

I will probably go ahead and try this no matter what, but I'm interested to hear what other more knowledgeable users think of this idea.

---

