---
title: "Theme Editing - Where do adjust progress bar?"
date: 2011-11-21
forum: General Help
---

### Post by Roasted on 2011-11-21
There's a theme I really like that I'm trying to alter a bit. I'm trying to change the shape of the progress bar so it has more rounded edges instead of being completely square. I'm curious if anybody else can look through this section of the one css page and see if anything in here is where the shaping it being dictated? It's been a while since I did css coding so I'm trying to re-learn as I go...

Thanks guys!

[http://pastebin.com/xmEcQymK](http://pastebin.com/xmEcQymK)

---

### Post by vasa1 on 2011-11-21
My uninformed money is on
```
border-radius: 0;
```

Maybe try increasing 0 to 1 or 2 or 3, etc.

A value of 0 gives me rectangular corners with scrollbars.

---

### Post by Roasted on 2011-11-21
Nice! I edited 3 lines within that blurb to match radius 8. Seems to have rounded the ends off nicely to make them a little more presentable. Subtle things.

Now to begin tinkering with rounding off the button corners just a hair...

Is it obvious I haven't done this before? ;)

---

### Post by vasa1 on 2011-11-21
> **Roasted said:**
> Nice! I edited 3 lines within that blurb to match radius 8. Seems to have rounded the ends off nicely to make them a little more presentable. Subtle things.

Now to begin tinkering with rounding off the button corners just a hair...

Is it obvious I haven't done this before? ;)

I'm totally an amateur with no formal knowledge but buttons may be little pics, png or gif or jpg. These may require editing with GIMP or Pinta or whatever? If they're svg, I'm not sure that ordinary mortals can tweak them :(

---

### Post by Roasted on 2011-11-22
Nah - I found out it was just a setting. If I recall it went something like:

border-radius: 0;

I adjusted it to 8 and it looks much better now.

---

