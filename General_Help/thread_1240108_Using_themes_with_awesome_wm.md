---
title: "Using themes with awesome wm"
date: 2009-08-14
forum: General Help
---

### Post by akrchstn on 2009-08-14
Okay, I have been using the default theme for a while now and I want to try a new one. I found [this theme]("http://awesome.naquadah.org/wiki/Zeb_theme") on the awesome wiki and I've been following [these instructions]("http://awesome.naquadah.org/wiki/Beautiful") but the only thing I really don't understand is this part ```
beautiful.init(os.getenv("HOME") .. "/.config/awesome/themes/default")
``` I can find the "beautiful.init(path_to_theme) section in my rc.lua but I just don't understand if I should put "beautiful.init(~/.config/awesome/themes/zeb/theme" or "beautiful.init(os.getenv("HOME")..."/.config/awesome/themes/default"
If it is the second one then I don't really understand what to put where the dots are supposed to be
This is the section of my rc.lua
```
-- The default is a dark theme
theme_path = "/usr/local/share/awesome/themes/default/theme"
-- Uncommment this for a lighter theme
-- theme_path = "/usr/local/share/awesome/themes/sky/theme"

-- Actually load theme
beautiful.init(~/.config/awesome/themes/zeb/theme)
```So far the ```
beautiful.init(~/.config/awesome/themes/zeb/theme)
``` method isn't working

---

### Post by aesa1983 on 2012-01-25
hi i really cant help you but maybe you can help me i usually am good at understanding this kinda things but in this case i think the syntax that they use in their wiki is just mind puzzling to me.

and my question is where are the files that need to be edited and am i not suppose to edit the original ones or what is going on here.? i would appreciate:D any kind of help you or anyone else who reads this can provide me with i need to them it  ):P

---

### Post by oldos2er on 2012-01-25
Closed, necromancy. Please start a new thread for your question or problem, and give as many details as possible.

---

