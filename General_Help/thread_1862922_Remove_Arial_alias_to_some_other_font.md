---
title: "Remove Arial alias to some other font"
date: 2011-10-17
forum: General Help
---

### Post by rachel1.0 on 2011-10-17
Hi! So, I just upgraded to Oneiric (actually reinstalled the whole thing) and something is bothering me, though I'm not completely sure if this is really new to Oneiric.

I started noticing different fonts in some sites (facebook for instance), and as a webdev, I always have firebug installed, so I decided to check, and saw that firefox is responding as if I had Arial installed. I don't - I really don't like that font hehe.

So, I did some google search and saw there's a command that gives me font aliases: fc-match.

```
rachel@rachel-laptop:~$ fc-match arial
LiberationSans-Regular.ttf: "Liberation Sans" "Regular"
rachel@rachel-laptop:~$ fc-match sans-serif
DejaVuSans.ttf: "DejaVu Sans" "Book"
```

So, I like DejaVu, but not so much liberation sans. And as a webdev, I'd prefer viewing sites with their next choice of font-family (usually it's going to be sans-serif, but you never know), since I *don't* have Arial.

I'd like to know if there's any way I could remove this alias that makes arial "available" in my system. And if not, how could I map it then to some other font.

---

