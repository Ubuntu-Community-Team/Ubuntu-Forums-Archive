---
title: "The license on the Serif font in Ubuntu 9.04"
date: 2009-07-10
forum: General Help
---

### Post by Grant A. on 2009-07-10
In the GIMP, I have the option of picking a font simply called, "Serif". Does anyone know what the license is on this font? I'd very much like to make a GPL v.2/CC-BY-SA dual licensed image with it.

---

### Post by CatKiller on 2009-07-10
By default, that would be Bitstream Vera Serif. You can read about its licensing [here]("http://www.gnome.org/fonts/"). The Serif generic is controlled by your font config; when applications ask for a Serif font they will be given a list of fonts in order, until one is found and used. You can control which fonts are made available with the /etc/fonts/conf.avail/40-generic.conf file.

---

### Post by Grant A. on 2009-07-10
> **CatKiller said:**
> By default, that would be Bitstream Vera Serif. You can read about its licensing [here]("http://www.gnome.org/fonts/"). The Serif generic is controlled by your font config; when applications ask for a Serif font they will be given a list of fonts in order, until one is found and used. You can control which fonts are made available with the /etc/fonts/conf.avail/40-generic.conf file.

Ah, thank you very much. :D

I have one question left, though.

Can I make a graphic with the Bitstream fonts, and license the resulting graphic under any license of my choosing?

---

### Post by CatKiller on 2009-07-10
> **Grant A. said:**
> Can I make a graphic with the Bitstream fonts, and license the resulting graphic under any license of my choosing?

I don't see why not, but then IANAIPL (I Am Not An Intellectual Property Lawyer).

The people that made the font only seem to be interested in how you distribute the font, not with what you create using the font.

---

### Post by Grant A. on 2009-07-10
> **CatKiller said:**
> I don't see why not, but then IANAIPL (I Am Not An Intellectual Property Lawyer).

The people that made the font only seem to be interested in how you distribute the font, not with what you create using the font.

Alright, thank you very much! :D

---

### Post by jenkinbr on 2009-07-10
Thanks, CatKiller - I was wondering the same thing when I saw this thread, so I susbscribed.

Nice info, and I didn't knwo that about serif being an alias to a list of fonts.  Thanks :)

---

