---
title: "Scrambled Words"
date: 2011-12-20
forum: General Help
---

### Post by ZCDW9 on 2011-12-20
Hi all,

Just installed 11.10.

All working fine now that I've got a small wireless networking issue out of the way. One minor niggle!

After a bit of use, the desktop background isn't as smooth, almost looking pixellated. In addition, some menus and pop-up words look a bit scrambled. 

Any ideas?

---

### Post by BC59 on 2011-12-20
Do you have installed the proprietary drivers for your graphics card?

---

### Post by ZCDW9 on 2011-12-20
Any ideas how I can check? I haven't installed any anyways. Think it's an integrated Intel chip.

Another example attached.

---

### Post by BC59 on 2011-12-20
Search for jockey on the dash. If there is an option for installing a driver activate it.

---

### Post by ZCDW9 on 2011-12-20
Nothing there unfortunately!

---

### Post by BC59 on 2011-12-20
So try to reset Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

sometimes after running you may still have problems and you need to run this command again
```
compiz --replace & disown
```

---

### Post by ZCDW9 on 2011-12-20
Worked after running, but after a restart the same problem again unfortunately.

---

### Post by BC59 on 2011-12-20
And this?

```
unity --reset
```

---

### Post by ZCDW9 on 2011-12-20
Same again unfortunately!

---

### Post by BC59 on 2011-12-20
Looks very strange! Did you try to change fonts to see if the situation changes? To change fonts you have to install the Advanced Settings from Ubuntu Software Center. Then search it from the dash.
And something else. From Ubuntu Center install the Ubuntu restricted extras, if you don't installed them already. They contain Windows TTF fonts.

---

### Post by ZCDW9 on 2011-12-20
Will try but not hopeful because it starts out ok and deteriorates over time. Quite confusing!

---

### Post by ZCDW9 on 2011-12-20
Still the same unfortunately!

---

### Post by ZCDW9 on 2011-12-20
Don't suppose anyone might have any other ideas? Bit of a nightmare this one, everything else works fine.

---

