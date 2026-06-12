---
title: "SVG output from Lilypond"
date: 2010-01-07
forum: General Help
---

### Post by Boldewyn on 2010-01-07
Hi,

I'm trying to get SVG output from Lilypond (lilypond.org), which I remember as straight forward 3 years ago when I last used it.

According to the docs, it would be as simple as

lilypond -fsvg music.ly

In lilypond 2.9 there was also the "backend" parameter:

lilypond -fsvg -bsvg music.ly

Well, on my Ubuntu 9.10 machine with ly 2.12.3, none of these work. Lilypond just runs, outputs happily an PS and finishes.

Do I need any extra library for SVG support or am I missing something else? Thanks for any hints!

---

### Post by Boldewyn on 2010-01-09
OK, it seems to be disabled and to come back in new glory with ly >= 2.13.4:

[http://old.nabble.com/No-svg-output---td25839338.html](http://old.nabble.com/No-svg-output---td25839338.html)

and

[http://wiki.lilynet.net/index.php/SVG_backend](http://wiki.lilynet.net/index.php/SVG_backend)

---

