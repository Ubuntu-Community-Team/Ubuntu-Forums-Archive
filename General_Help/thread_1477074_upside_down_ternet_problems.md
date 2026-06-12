---
title: "upside down ternet problems"
date: 2010-05-08
forum: General Help
---

### Post by lotacus on 2010-05-08
I followed the how-to on the ubuntu wiki and it would crash squid.

did a little research and came to the conclusion that squid needed the location of perl.

I modified the line so it read:

url_rewrite_program /usr/bin/perl /usr/local/bin/flip.pl

squid launched fine, however the images that are supposed to be flipped are all broken.

when going to /var/www/images/ I noticed that there is nothing in there for morgify to modify.

Does anyone know what may be going on and have a solution to get it to work?

---

### Post by musik4u66 on 2011-11-15
Hey I'm having the same issues that you are having. Everything is working properly but the images aren't being flipped. At first the images were broken, but now they are fine. Did you ever figure out how to solve this? Please I really need to know, i've been working at this for days now.

---

