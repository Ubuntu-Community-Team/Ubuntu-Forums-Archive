---
title: "Ubuntu Font Problems"
date: 2009-09-14
forum: General Help
---

### Post by Loafers on 2009-09-14
I am about to reinstall Ubuntu for the third time because of font problems.

Every time I have installed a package that has fonts included such as mscorettfonts or WINE, my fonts ***_ALWAYS ALWAYS ALWAYS_*** GET MESSED UP, which is no problem because I can always remove it.  Wishful thinking actually.

I tried sudo dpkg --purge ttf-arphic-uming ttf-kochi-gothic ttf-kochi-mincho ttf-thai-tlwg ttf-arabeyes ttf-indic-fonts-core ttf-lao ttf-malayalam-fonts ttf-unfonts-core mscorettfonts

and they still look the same... Yes I'm being anal, but ubuntu fonts/font rendering is the best I have ***_EVER_*** seen and anything less hurts my eyes.

Here is an example:

Before:

[IMG]http://i27.tinypic.com/23tfsp4.png[/IMG]

After:

[IMG]http://i25.tinypic.com/acajr5.png[/IMG]

Smaller, cramped, and angular, the new fonts JUST WON'T GO AWAY :(!!

Any suggestions before I reinstall?

---

### Post by Vaphell on 2009-09-14
probably this happens because websites use some font-families or even exact windows font names to define formatting and windows fonts happen to take precedence over ubuntu ones.

In firefox preferences you can configure fonts for 4 main categories: proportional, serif, sans-serif and monospace. Personally I set them to point at proper DejaVu flavors. I also disallowed using different fonts by the webpages and set minimum and default size.
Granted, not every page is pretty, but it's unavoidable either way in a world where web developers test their stuff exlusively on windows.

---

### Post by Loafers on 2009-09-14
> **Vaphell said:**
> probably this happens because websites use some font-families or even exact windows font names to define formatting and windows fonts happen to take precedence over ubuntu ones.

In firefox preferences you can configure fonts for 4 main categories: proportional, serif, sans-serif and monospace. Personally I set them to point at proper DejaVu flavors. I also disallowed using different fonts by the webpages and set minimum and default size.
Granted, not every page is pretty, but it's unavoidable either way in a world where web developers test their stuff exlusively on windows.

Wow, worked like a charm ](*,)  They look exactly like the default fonts before installing the programs that include messed up the fonts. Thanks you so much!

Also by any chance do you know what "proportional" type means?

Regards,
Loafers

---

### Post by Vaphell on 2009-09-14
proportional is the opposite of monospace
[http://en.wikipedia.org/wiki/Typeface#Proportion](http://en.wikipedia.org/wiki/Typeface#Proportion)

you decide which one will be your default 'pretty' font, serif one or sans-serif one

---

