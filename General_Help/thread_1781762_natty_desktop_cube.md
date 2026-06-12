---
title: "natty desktop cube"
date: 2011-06-14
forum: General Help
---

### Post by link15 on 2011-06-14
[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty) I tried the "alternative GUI way" and it worked!, until I shut down the computer, and when I turned it back on it wouldn't display the unity gui at all, so is there a way to open ccsm without the unity launcher t undo everything I did (I've tried it in ubuntu classic, and unity 2d, but they all have there own compiz configs)

---

### Post by dFlyer on 2011-06-14
Can't answer your question, I don't use the cube, but this has been discussed multiple time on the forum. Do a search and you may find and answer,

---

### Post by mc4man on 2011-06-14
This is the way I always switch from wall to rotate/cube, then afterwards go into ccsm and adjust the viewport switcher, ect.

(also useful to disable some other plugins that sometimes unset all the plugins.
gconf should be used carefully for enabling - it doesn't do conflict resolution, I use it to enable a couple other than rotate/cube like Text

[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

---

### Post by link15 on 2011-06-14
THANK YOU!!!:popcorn: the link helped

---

### Post by mc4man on 2011-06-14
> **link15 said:**
> THANK YOU!!!the link helped
Once you get it set up as far as what plugins you basically want you can get yourself a list for future reference like this

```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins
```
Then copy the result out and save in a file somewhere
Ex. my current set on natty

~$ gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugin 
[COLOR="Blue"][core,composite,opengl,decor,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell][/COLOR]


Now while I'm not really recommending - if I was messing around and wanted to reenable that set I'd use the blue in a set command - EX.

The set command
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins [COLOR="Blue"][blue here][/COLOR]

Like - 
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  [COLOR="Blue"][core,composite,opengl,decor,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell][/COLOR]
```

Though after a while you tend to remember them all and you can slowly add back in ccsm, waiting for it to reset after ecery one or two ect.

---

