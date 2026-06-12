---
title: "non free fonts only in Openoffice"
date: 2006-02-10
forum: General Help
---

### Post by Denis on 2006-02-10
Hi I wanted to contribute this small hint.

There are many topics discussing how to get Microsoft non free fonts with your ubuntu system. But the downside of installing the msttcorefonts package is that it installs the fonts system wide. 

I didn't like that, because Firefox e.g. will also use these fonts then. 

So to get these fonts in Openoffice only you'll have to download and install the msttcorefonts package (temporarily) to get the fonts (of just copy them from another location). 

Instead of moving them to ~/.fonts, you place them in /usr/lib/openoffice2/share/fonts/truetype. 

Start Openoffice and the fonts will be in your list. Maybe you will have to reconfigure the default fonts (in tools -> options ->OO.org writer -> basic fonts)

I found some documentation about the fonts path here: [http://www.openoffice.org/FAQs/fontguide.html#5](http://www.openoffice.org/FAQs/fontguide.html#5)

So maybe this can be of any help fore someone.

---

### Post by dcstar on 2006-02-10
[QUOTE=Denis]Hi I wanted to contribute this small hint.
.......
So maybe this can be of any help fore someone.[/QUOTE]

Please post this in the "Customization Tips and Tricks" forum.

---

