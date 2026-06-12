---
title: "Too many wine entries"
date: 2010-06-28
forum: General Help
---

### Post by pulseplanet on 2010-06-28
Hello Everyone,

  I recently had trouble with some wine installation and completely reinstalled wine. Now when I right click on a file and select "Open with" I see too many entries with "A Wine Application". How do I clean up all these entries?
 
  See screen shot below:
[IMG]http://img811.imageshack.us/img811/7186/97221694.png[/IMG]

Many thanks
KB

---

### Post by philinux on 2010-06-28
[http://ubuntuforums.org/showthread.php?t=642961](http://ubuntuforums.org/showthread.php?t=642961)

---

### Post by dino99 on 2010-06-28
with nautilus, open .wine folder (hidden, ctrl+h) and remove the unwanted entries

---

### Post by Lykopis on 2010-06-28
Yeah: I have the same issue, except it's the name of an app that runs under wine.
I am sure there is a text file somewhere you could edit to remove the extra entries,
But I have yet to find it.

---

### Post by Lykopis on 2010-06-28
xx

---

### Post by pulseplanet on 2010-06-28
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=642961](http://ubuntuforums.org/showthread.php?t=642961)

**SOLVED**

philinux, thanks for the pointer. Following your link, 
I did "rm -f ~/.local/share/applications/wine*.desktop" and the "Open With" menu now looks clean. 

I guess this was ok for me (deleting all entries) only because I am reinstalling wine and all the applications under wine again.

Once again, thanks.

---

### Post by philinux on 2010-06-28
Good stuff.

Please mark the thread as Solved.

Use the **[COLOR="Red"]Thread Tools [/COLOR]**pull down menu.

---

### Post by Lykopis on 2010-06-28
Thanks guys That really helped.
Sorry about the double post earlier for some reason my wireless connect dropped out.

---

