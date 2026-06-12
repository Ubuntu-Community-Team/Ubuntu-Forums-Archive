---
title: "how to configure Brightness"
date: 2006-04-27
forum: General Help
---

### Post by ozkan on 2006-04-27
my screeen  is too bright how can i fix it

---

### Post by antivert on 2006-04-27
I assume this is a notebook? On my wife's notebook using Ubuntu it was automagically configured to be fn-F5/fn-F6 to darken/brighten.

---

### Post by Jagot on 2006-04-27
Yep, mine's FN+arrow down.  If you don't have a nice informative icon on whichever key it is then consult your manual.

---

### Post by ozkan on 2006-04-27
they didn't worked, can i do it by a software ?

PS: it's a laptop

---

### Post by Jagot on 2006-04-27
Can you tell us what laptop it is please?

---

### Post by ozkan on 2006-04-27
my laptop is sony vaio VGN-BX196VP

---

### Post by DoktorSeven on 2006-04-27
All else fails use xgamma

```
xgamma -gamma 0.8
```

default is 1.0, fractional values less than 1 darken, greater than 1 brighten.

---

### Post by unnes on 2006-04-27
I have a very dim display, so i use xgamma -gamma 2.7 to bring it up to an acceptable brightness (albeit with some washed out colors).

xgamma should be useful for you as well... for all the modifiers check out > man xgamma

---

### Post by knefas on 2006-04-30
[QUOTE=ozkan]my laptop is sony vaio VGN-BX196VP[/QUOTE]
xgamma only change what you see, but it doesn't actually dimm the screen, i.e. your battery life will be the same.

For vaios you can see spicctrl and nvclock (0.8beta, command line nvclock -S). I'm not sure which one could work with your laptop, just try. :-)

---

### Post by stojan on 2006-04-30
In my laptop it's combination of fn+F1/F2...Try all combinations with fn and you will see ;)

---

### Post by ozkan on 2006-04-30
it was a sticctrl but it didnot worked too. I think I have a problem with my computer . my sony vaio VGN-BX196VP can even close/restart itself with linux  OS . it can not interrupt the card. i installed spicctrl but it does nothing spicctrl -B(for getting brightness) is always 0,even i set it to 255 .  i tried all combiantions with Fn but nothing works !!!

](*,)

---

