---
title: "Newbie: gedit plugins installation..."
date: 2009-09-03
forum: General Help
---

### Post by gf_gollum on 2009-09-03
- I'm trying to install a simple cTags plugin into gedit but the instructions don't seem to work for me. I've ended up scattering files across my hard drive - and nothing seems to work - so I'm asking for help please

Plugin is:  the gedit symbol plugin from [here]("http://www.micahcarrick.com/11-14-2007/gedit-symbol-browser-plugin.html") 

Looks nice - but doesn't seem to work./ I'd appreciate a more step by step explanation if possible please
Thx
Graham
(ex- Windows user :-) No ubuntu 9.04 on MSI Wind netbook.

---

### Post by Vaphell on 2009-09-03
gedit plugins are to be found in ~/.gnome2/gedit/plugins

i've installed regex-replace plugin there and it works just fine.

```
cp gedit-symbol-browser-plugin*.tar.gz ~/.gnome2/gedit/
tar -xzf gedit-symbol-browser-plugin*.tar.gz
```
this part of install instructions indicate that too

EDIT:
i installed it and got additional tab on the left side of gedit
i went there -> [http://sourceforge.net/projects/symbol-browser](http://sourceforge.net/projects/symbol-browser)
and picked binary version (in my case for AMD64)

there were 2 directiories: plugins and sybmols
i put them into ~/.gnome2/gedit/
i went to preferences, checked plugin to be enabled - voila!

i can't say if it works, i don't know really what it is supposed to do

---

### Post by gf_gollum on 2009-09-03
Thanks for the rapid response. You make me take stock of what I had done.. and I hadn't downloaded the ubuntu binary file - just the regular one (which looked like source code!!)
Thx
Graham

---

