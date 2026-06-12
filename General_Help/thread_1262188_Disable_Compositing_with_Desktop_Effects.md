---
title: "Disable Compositing with Desktop Effects"
date: 2009-09-09
forum: General Help
---

### Post by hwttdz on 2009-09-09
I'd like to be able to use the scale addons, and the rotate desktop cube and a few other goodies, but I do not want to have compositing (it interferes with graphics of some programs I use).  How can I turn off compositing without disabling desktop effects entirely?  Thanks.

---

### Post by earthpigg on 2009-09-09
unfortunately, you cannot. the act of displaying these goodies on your screen _*is*_ compositing.

*however,*

this is what i do:

alt+f2, and run "metacity --replace" will turn compiz/compositing off.

alt+f2, and run "compiz --replace" will turn compiz/compositing back on.

very quick. if you want to do some learning, you can make a shell script and put it on your desktop. one icon as your 'on' button, another as your 'off' button.


you can also install fusion-icon... it keeps a little icon in your system tray that you can click to enable/disable compiz/compositing/desktop effects (all three are the same, for our purposes) quickly.

---

### Post by hwttdz on 2009-09-09
I thought compositing was just the bit that was responsible for managing window transparency?  Is there a way I can turn off just that bit?

If I remember correctly at one point I was able to disable the transparency part and get it to work while also having some of the other goodies.

---

### Post by earthpigg on 2009-09-09
if it is just certain compiz plugins that are messing with the other software you are running, then you can go ahead and disable just those plugins.

---

