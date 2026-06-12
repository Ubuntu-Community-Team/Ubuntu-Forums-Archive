---
title: "cheese starts upon startup"
date: 2010-08-26
forum: General Help
---

### Post by Paul S on 2010-08-26
I can't find a way to use cheese in lucid.  When I start it, it immediately starts flashing photos in countdown mode and repeats.  I can't find a way to stop it except to use the hardware Fn-Esc to disable the webcam.

Because of the intermittent flashing and countdown 3-2-1 screens, I can't hit any buttons or menus.

What is wrong and how can I fix it?

TIA

---

### Post by Paul S on 2010-08-26
OK, upon searching my home directory, I find this file .gconf/apps/cheese/%gconf.xml 

By trial and error, I find that changing this line 

```
<entry name="burst_repeat" mtime="1282353584" type="int" value="3"/>
```

to this:

```
<entry name="burst_repeat" mtime="1282353584" type="int" value="2"/>

```

Now cheese behaves like a normal program.

---

