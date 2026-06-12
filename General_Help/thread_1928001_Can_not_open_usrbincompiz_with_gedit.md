---
title: "Can not open /usr/bin/compiz with gedit"
date: 2012-02-19
forum: General Help
---

### Post by dctrsatan on 2012-02-19
This is what I get:

[IMG]http://i249.photobucket.com/albums/gg213/killallmormons/Screenshot.png[/IMG]

This is what I am trying to achieve:

It seems that Intel GM 965 series have been blacklisted in compiz

open the file : sudo gedit /usr/bin/compiz

change the line : T="$T 8086:2a02 " # Intel GM965

to : # T="$T 8086:2a02 " # Intel GM965

save it and compiz can work again.

---

### Post by nothingspecial on 2012-02-19
never mind

---

### Post by MG&amp;TL on 2012-02-19
Compiz is an executable; where did you find this information? Possibly this will work, but I doubt it.

You could use Bless binary editor. But I can't find any reference to that string in the file:

```
cat /usr/bin/compiz | grep 8086

```

---

### Post by nothingspecial on 2012-02-19
Before you mess about with that, where did you get this information?

That is extremely risky.

---

### Post by MG&amp;TL on 2012-02-19
> **nothingspecial said:**
> Before you mess about with that, where did you get this information?

That is extremely risky.

To be fair, if compiz isn't working anyway, what's he or she going to lose? But I agree, modifying compiled executables is generally not a good idea.

---

### Post by dctrsatan on 2012-02-19
[http://ubuntuforums.org/archive/index.php/t-1469658.html](http://ubuntuforums.org/archive/index.php/t-1469658.html)

---

### Post by dctrsatan on 2012-02-19
I do not care anymore I accept that this chip will not work properly with the compiz program oh well.

---

