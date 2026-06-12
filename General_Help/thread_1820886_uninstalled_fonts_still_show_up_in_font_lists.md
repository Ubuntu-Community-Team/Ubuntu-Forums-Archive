---
title: "uninstalled fonts still show up in font lists"
date: 2011-08-08
forum: General Help
---

### Post by Mahkoe on 2011-08-08
So if you've seen any of my other posts you know I'm a bit of an idiot, but I gotta ask anyway;

So I install a font, don't like it, then uninstall it. Simple enough, but when I say a font, I mean the 465 free true type fonts by Brian Kent. For some reason I thought it had said 45 and thought that font options would be nice. Of course, hardly any of the fonts were worth using, so I uninstalled them. Yet, their names still show up in the list of fonts in all programs that use a font list. There are 465 names that don't have a font associated with them, and it's driving me nuts. Any ideas?

Ubuntu 10.10 32 bit

---

### Post by SalHelder on 2011-08-08
How did you uninstalled them? Did you removed them from the .fonts folder?

---

### Post by Mahkoe on 2011-08-08
Yes. Was that the wrong way?

---

### Post by SalHelder on 2011-08-08
Actually thats how you should have done it, anyway check the folders:

/usr/share/fonts
/usr/local/share/fonts

To see if they are there. If so open nautius as root:

su -
nautilus

And remove the fonts that you don't want (I'd recommend you NOT to touch the fonts that are not those that you want to remove).

If it still fails, try installing font-manager:

sudo apt-get install font-manager

You'll find it in Applications > Graphics

And see if you can remove them that way.

---

### Post by Mahkoe on 2011-08-08
Thanks

---

