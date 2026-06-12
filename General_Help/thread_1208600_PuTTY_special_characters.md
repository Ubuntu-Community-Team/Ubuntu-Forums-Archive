---
title: "PuTTY special characters"
date: 2009-07-09
forum: General Help
---

### Post by Dagur on 2009-07-09
Hi,

I have Ubuntu server 9.04 installed and SSH enabled. When I connect to it with my ubuntu desktop I have no problems but if I connect through PuTTY on my windows workstation I have problems with special characters (namely þ,æ,ö,ð and more. All iso-8859-1 characters).
On the console they display correctly but they don't appear when I press the key on the keyboard, they only appear after I've pressed some other key (like it's waiting).
If I open up an editor like vi or pico these characters appear as gibberish (æ is ï¿½ for example).

I've installed every version of ubuntu server on that computer since the first one and this hasn't happened before.

---

### Post by geirha on 2009-07-09
You want to go into putty's options and make sure the character encoding is set to utf-8.

[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-translation](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-translation)

---

### Post by Dagur on 2009-07-09
> **geirha said:**
> You want to go into putty's options and make sure the character encoding is set to utf-8.

[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-translation](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-translation)

That was painfully simple. I was looking for a setting like this under "keyboard" in putty.

Thanks! :guitar:

---

