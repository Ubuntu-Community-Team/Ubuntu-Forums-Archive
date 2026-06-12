---
title: "Text Editor with Transparent Background?"
date: 2012-07-16
forum: General Help
---

### Post by neu5eeCh on 2012-07-16
Outside of terminal text editors, are there any text editors that offer a transparent background and solid text (like what the terminal gives you)?

---

### Post by sudodus on 2012-07-16
I don't understand what you mean by 'outside of', but maybe you would be interested in ***tilda***

```
sudo apt-get install tilda
```

---

### Post by neu5eeCh on 2012-07-16
Thanks, I forgot about tilda. What I meant by "outside of" was "besides". Are there any text editors like leafpad, for example (editors that are not in terminals) that offer transparent backgrounds?

---

### Post by sudodus on 2012-07-16
I see. No, I don't know any text editor or word processor with transparent background. I think it would be rather confusing, but you might need it for a special reason. If you find nothing else, and you can stand editing with nano, vim or emacs -nw, you can do that in a tilda window. Emacs comes from unix, it is very advanced but has a steep learning curve.

---

### Post by neu5eeCh on 2012-07-16
> **sudodus said:**
> I see. No, I don't know any text editor or word processor with transparent background. I think it would be rather confusing...

Yes, but it looks **so** cool. :cool: I'll just have to learn how to use VIM.

---

### Post by sudodus on 2012-07-16
> **VTPoet said:**
> Yes, but it looks **so** cool. :cool: I'll just have to learn how to use VIM.

Vim is a user friendly version of old vi (also from unix). It is very different from most modern editors, but I know people who really like it. They say that when you get used to it, vim is very efficient.

Good luck :-)

---

### Post by Toz on 2012-07-16
VTPoet, I'm not sure if your still using Xfce, but if so, you can use transset with Xfce's compositor to change the transparency of any window. First you'll need to install the transset package if not already installed. Startup your text editor. Then Alt+F2 and run:
```
transset x
```
...where x is a value from 0.0 to 1.0 in decimal increments (0 = transparent, 1 = opaque). Click Run and your mouse pointer will change to a + (plus sign) then click the window you want "transparentized".

---

### Post by LewisTM on 2012-07-16
Another way to do it in Xfce is to hover your mouse over the title bar, hold down the Alt key and modulate the window opacity with the mouse wheel. You text will also be dimmer but at least you will see what's underneath. Go ghost windows!

Cheers!

---

