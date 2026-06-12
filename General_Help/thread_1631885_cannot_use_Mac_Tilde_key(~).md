---
title: "cannot use Mac Tilde key(~)"
date: 2010-11-27
forum: General Help
---

### Post by Skywalker# on 2010-11-27
Hello,

I have installed Ubuntu 10.10 meerkat on My Macbook 5,1 and all is ok so far.

One thing I have noticed is I cannot type the tilde key how I normally do using SHIFT and then the button to the right of shift on my macbook keyboard. I have tried the UK and USA Macintosh keyboard option with no luck.

As you can see my forum login uses the tilde key. I have to copy and paste the character. I cannot even see it in the character map.

How do others get around this?

Any idea's?

Many thanks,

Luke

---

### Post by eric3_14159 on 2010-12-24
Although I have no idea what is causing this, I have one possible solution.

Run the command "xev" (in the package x11-utils). It outputs all the information about events going to the X server you could ever want to know.

Position the mouse in the black box in the window that is opened, and type tilde. Do not move the mouse, and in the mess of output that is created, write down the keycode and keysym which appear. Hopefully, unique numbers are printed, and you can then use xmodmap, which has a fairly comprehensive man page, to correctly bind the key to the tilde character.

Good luck.

---

