---
title: "Dockbarx minimized icons grayed out"
date: 2009-11-15
forum: General Help
---

### Post by xxhopingtearsxx on 2009-11-15
Does anyone know how I can make minimized DockbarX windows show their color? It's hard to see when the icons of minimized windows are just a dark gray. Here's an example

[IMG]http://i33.tinypic.com/2ypjity.png[/IMG]

---

### Post by xxhopingtearsxx on 2009-11-15
bump

---

### Post by nortexoid on 2009-11-15
I'm curious about disabling this "feature" too. Especially the feature that just partially greys icons out when you have multiple instances/windows of a single app open.

---

### Post by M7S on 2009-11-17
To remove the greyed out icons on dockbarx you can either find yourself a theme with an minimize effect you like (it's a useful feature imho ;) or edit out the minimize effect from the theme you are using.

You can edit out the feature from the theme by editing the config file in your theme file (you'll find it in /usr/share/dockbarx/themes or ~/.dockbarx/themes). Simply remove every <if type="all_minimized"></if> and everyting in between those. Do the same for <if type="some_minimized"></if> (if you only want to remove that partially grey you should only remove these not the "all_minimized" ones).

I hope these instructions where clear enough.



M7S,
Dockbarx developer.

---

### Post by xxhopingtearsxx on 2009-11-17
Thank you so much!

---

