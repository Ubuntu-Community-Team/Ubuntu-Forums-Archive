---
title: "Fontforge crashes when generating SOME fonts"
date: 2011-09-28
forum: General Help
---

### Post by Dingbats on 2011-09-28
I've extracted a font from a PDF, in Fontforge, and added the å character (copied an a and added the circle).  When I try to generate a truetype font from this, it crashes, **if** I keep that å.  If I remove it, it works fine.

On startup in a terminal, it says:

```
Help! Server claimed font
	-dejavu-dejavu serif-medium-o-normal--15-0-0-0-p-0-iso8859-2
 existed in the font list, but when I asked for it there was nothing.
 I may crash soon.
Help! Server claimed font
	-dejavu-dejavu serif-medium-o-normal--15-0-0-0-p-0-iso10646-1
 existed in the font list, but when I asked for it there was nothing.
 I may crash soon.
```

Over and over lots of times.  Then it segfaults when I hit "generate".  I've run fc-cache and some other commands I googled up, but to no avail.  There is no file called fonts.dir in any subdirectory of /usr/share/fonts.

Version data:

```
Copyright (c) 2000-2009 by George Williams.
 Executable based on sources from 23:48 GMT 23-Sep-2009.
 Library based on sources from 17:32 GMT 14-Sep-2009.
fontforge 20090923
libfontforge 20090914
```

I've also experienced crashes seemingly at random from doing things like pressing ctrl in the glyph editor.

Any ideas?

---

### Post by Dingbats on 2011-09-29
Bomp...

---

