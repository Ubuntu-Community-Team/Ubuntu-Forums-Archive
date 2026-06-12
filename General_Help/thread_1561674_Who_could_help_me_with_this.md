---
title: "Who could help me with this?"
date: 2010-08-26
forum: General Help
---

### Post by 1antares1 on 2010-08-26
Hello again friends, I have problems with fonts in Ubuntu.

With the kind of letters / "Sources" and install the msttfonts and I still have problems.

Install the Tahoma and is still displayed in a horrible manner.

What I can do to return to the above sources or the default fonts used by websites, as seen in Windows XP.

Does anyone have knowledge on this? Since no one even helped me and really I appreciate it, thanks.

A catch as you can see the sites.

[SIZE=3][COLOR=Red]**1.) **[/COLOR][/SIZE][http://casidiablo.net/como-ayudar-a-otros-a-migrar-a-gnulinux/](http://casidiablo.net/como-ayudar-a-otros-a-migrar-a-gnulinux/)



[IMG]http://i36.tinypic.com/2dslt9f.png[/IMG]


[SIZE=4][COLOR=Red]**2.) **[/COLOR][/SIZE][www.vBulletin.com/forum]("http://ubuntuforums.org/www.vBulletin.com/forum")

[IMG]http://i37.tinypic.com/35bsh05.png[/IMG]

[SIZE=4]

[/SIZE][CENTER][SIZE=4][COLOR=Red]**Anybody would be so kind as to look at my problem?**[/COLOR][/SIZE]

:frown:
[/CENTER]

[COLOR=RoyalBlue]**Really, I appreciate it. :(**[/COLOR]

---

### Post by quixote on 2010-08-28
I'm not quite sure what you've done so far.  Did you install msttcorefonts using synaptic?  Or did you download source code and try to do it that way?  If you look in /usr/share/fonts/truetype, is, for instance, tahoma.ttf listed there?

If you install fonts manually, you have to update the font-cache before the system can use them.  (Yeah, kind of stupid, I know.)```
sudo fc-cache -f -v
```

---

### Post by 1antares1 on 2010-09-12
):P

Gracias hermano, tema solucionado! ;) Eso era, tenía que limpiar el caché y ésta vez lo instalé desde el Repositorio. El único que me contestó ;)

Saludos!

---

### Post by quixote on 2010-09-15
My Spanish is not too good, but I gather that solved the problem?  Hope so! :biggrin:

---

