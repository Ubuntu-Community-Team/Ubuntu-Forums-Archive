---
title: "Customized keyboard layout isn't listed in Preferences/Keyboard"
date: 2011-03-03
forum: General Help
---

### Post by edonan on 2011-03-03
Hi, I defined a variant to my keyboard layout (Italian) editing the file */usr/share/X11/xkb/symbols/it* and adding this block:

```
partial alphanumeric_keys
xkb_symbols "itaro" {

    include "it(basic)"

    name[Group1]="Italy - Romanian accents";

    key <AC01>	{ [ a, A, abreve, Abreve ] };
    key <AD01>	{ [ q, Q, acircumflex, Acircumflex ] };
    key <AD08>	{ [ i, I, icircumflex, Icircumflex ] };
    key <AD05>	{ [ t, T, 0x100021b, 0x100021a ] };
    key <AC02>	{ [ s, S, 0x1000219, 0x1000218 ] };

};
```

This customization provide the variant "itaro" to the Italian keyboard layout. I can set the layout by the command line typing "setxkbmap it itaro", I see it works because after that I can type &#259;, &#258;, &#539;, &#538;, etc. using Alt-gr. But I can't choose this variant in the Keyboard Preferences dialog because it isn't listed at all (I reloaded X-Window of course).
Any hints?
Thank you.

PS: I'm using Jaunty if this matters.

---

### Post by edonan on 2011-08-12
I managed to get it work in gnome (now I can switch layout from System/Preferences/Keyboard). It is pretty simple if you know what to do.

I had to edit some files in /usr/share/X11/xkb/rules/:

In both **base.lst** and **evdev.lst** I put:
```
  itaro           it: Romanian accents
```

and in both **base.xml** and **evdev.xml** I put:
```
        <variant>
          <configItem>
            <name>itaro</name>
            <description>Romanian accents</description>
          </configItem>
        </variant>
```
**_Note that_** the code above must be placed inside the <variantList> ... </variantList> block of your layout (in my case "it").

You shouldn't need to reload X, just open the Keyboard preferences and it should list the new layout variant.
Credits: [http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

---

