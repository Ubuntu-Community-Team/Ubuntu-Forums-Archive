---
title: "I accidentally removed all my toolbars in FF..."
date: 2009-11-06
forum: General Help
---

### Post by blur xc on 2009-11-06
Does anyone know how to get them back?

I was playing around with some add-ons to increase verticle space, and accidentally removed my menu bar, navigation bar, and bookmark bar.  Now I'm barless and don't exactly know how to get them back.

Thanks,
BM

---

### Post by akand074 on 2009-11-06
Right click on the top bar where "File, Edit, View etc. is, check the "Navigation Toolbar" and "Bookmarks Toolbar" checkbox. Or is that bar gone as well? If so the alt key should temporary bring it back I believe?

---

### Post by kio_http on 2009-11-06
Menu > Accessories > Terminal

type 

rm -rf /home/yourusername/.mozilla


Replace yourusername with the name of your user account

(edited to say .mozilla) Thanks for pointing out, I'm not actually a Firefox user.

---

### Post by akand074 on 2009-11-06
> **kio_http said:**
> Menu > Accessories > Terminal

type 

rm -rf /home/yourusername/.firefox


Replace yourusername with the name of your user account

That works too lol, except it resets your profile and it would be as if you first opened firefox for the first time. It doesn't seem like thats a problem for you though

---

### Post by fooman on 2009-11-06
> **kio_http said:**
> Menu > Accessories > Terminal

type 

rm -rf /home/yourusername/.firefox


Replace yourusername with the name of your user account

should be .mozilla *not* .firefox  ;)

---

