---
title: "Samba mount pulling from multiple directories?"
date: 2010-10-21
forum: General Help
---

### Post by matthew.parlette on 2010-10-21
I'm looking to see if this is possible, but my web searches haven't come up with anything yet:

I have a TV share right now (/media/TV), which is shared through samba as TV. I just got a new hard drive to have more space for shows, which I plan to mount as /media/TV2.

What I would like, however, is to have a single TV samba share that points to both /media/TV and /media/TV2.

I have a few other applications for this, but this is the pressing one right now. I found [[COLOR="Blue"]greyhole[/COLOR]]("http://code.google.com/p/greyhole/"), which kinda does what I'm looking for, but it looks a little more involved that what I would be trying to do. I'll keep reading about it, but I wanted to see if anyone has done anything like this already.

---

### Post by HereInOz on 2010-10-21
Why not mount the second hard drive into a folder in /media/TV so it becomes, say, media/TV/TV2

Does that do the job?

---

### Post by matthew.parlette on 2010-10-21
Hm, that's a nice option. To make it a little more uniform, I'd probably have the /media/TV folder shared as TV, then in there have /media/TV/TV and /media/TV/TV2.

I'm not sure off the top of my head if XBMC will read that correctly, but I'll give it a shot tonight and report back. Thanks for the suggestion.

---

