---
title: "wget jpeg/thumbnail linking problem"
date: 2010-05-30
forum: General Help
---

### Post by galenh on 2010-05-30
Evening all,

I'm putting my way around wget right now, and I'm having a bit of a problem figuring out how to word a certain command. I have a URL which holds thumbnail links to 32 images (I'm using it to test wget-- it's [http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search](http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search)). I'm attempting to get the 1280x800 jpg versions of the images through the thumbnails on the linked page.

So far I have tried:

~$ wget -A jpg [http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search](http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search)

(Which allows me to just get jpegs, but it only gave me the thumbnails from that page, understandably)

Then came this:

~$ wget -r -A jpg [http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search](http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search)

(Same as above, but recursive)

Finally:

~$ wget -r -H -A jpg [http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search](http://www.4walled.org/search.php?tags=awesome&board=&width_aspect=1280x160&searchstyle=larger&sfw=0&search=search)

(Adding the ability to follow external links. I figured THAT would bring me to at least the next page AFTER each thumbnail, but to no avail.)

I've checked all over, and found many helpful tips about general usage of wget, but never this one specified (surprisingly). The wget wiki is a bit... bare at the moment, so I figured I'd ask here.

Thanks

---

### Post by srbrunoaf on 2010-12-26
Hope I'm not raising a dead thread? It was unanswered, so...

This is my first post, just made an account because I found this thread with the same doubt and there was no help, and since I managed to get the answer on my own, well...

I was with the same problem with wget and 4walled, and kept trying, and this is what I got, not perfect, but works:

wget -rp -R=php --span-hosts --domains=4walled.org --exclude-directories=thumb -d [http://4walled.org/search.php?tags=scenic+landscape+city+scenery+plain+texture+abstract&board=&width_aspect=1440x160&searchstyle=larger&sfw=0&search=random](http://4walled.org/search.php?tags=scenic+landscape+city+scenery+plain+texture+abstract&board=&width_aspect=1440x160&searchstyle=larger&sfw=0&search=random)

-r (recursive)
-p (images)
-R=php (I don't want those phps)
--span-hosts (check other hosts)
--domains=4walled.org (only this host, actually, not ads and stuff)
--exclude-directories=thumb (don't waste time with that)
-d (debug, can remove it now, I guess, used until I could get it right)

Plus the adress, some nice walls (1440x900) there, except for a bunch of "abstract, blue" tagged walls which are neither abstract nor blue (some garbage/NSFW).

This command I made is far from perfect: it downloads 65 items (480 KB) of garbage plus the walls, but I hope this helps you.


Now I think I'll try to make a wallpaper changer script ;)

---

### Post by ThermalSloth on 2011-06-21
I'll give this a nice and shiny bump, sorry about that.

The reason wget is not working, is because of our (poor) anti-hotlinking protection.
4walled is already burning through 3TB or more monthly,
and since bandwidth costs money.. :)

tl;dr: You're doing it wrong, needs the right referrer.

---

