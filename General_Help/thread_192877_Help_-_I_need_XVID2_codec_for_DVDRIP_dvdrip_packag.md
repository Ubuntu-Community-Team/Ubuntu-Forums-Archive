---
title: "Help - I need XVID2 codec for DVD::RIP dvdrip package"
date: 2006-06-09
forum: General Help
---

### Post by rpesq on 2006-06-09
Hi,

Can anyone help me find/install "XVID2", which is one of the encoding options in the dvd::rip program?  When I used Suse 10.0 or 10.1, the libxvidcore.so.2 package was available in YAST, so it was easy to get.  I think that is what I downloaded to get xvid2 working in Suse.

I believe that "Xvid2" is also called Xvid 0.9.2, and pretty much an open-source equivalent to Divx5.  

I tried to copy the libxvidcore* files from my Suse partition, but that is not working for me.  Maybe I am doing something wrong, or maybe I am not copying all the files that I need....

I need Xvid2 because it is the most compatible with my set-top dvd/divx player (Philips dvp-642).  The other codecs do not work as well for my needs. 

Just so that their is no misunderstanding, I can PLAY xvid files fine on my PC.  I need to be able to ENCODE my videos into "xvid2" inside dvd::rip application.  Right now, as DVD::RIP is installed with Automatix, I only have the option to use xvid and xvid4.  (with xvid2 and xvid3 missing, but xvid3 I do not need.)

Any help getting XVID2 enabled will be MUCH APPRECIATED.  Thanks in advance, and long-live-Ubuntu!

---

### Post by grendelkhan on 2006-06-09
Make sure you have the universe and mulitverse repositories enabled and you can just apt-get libxvidcore4.

---

### Post by rpesq on 2006-06-09
Hi,

I have libxvidcore4, but it only provides "xvid4", ...or at least that is all that it installed on my system.  I do have the extra repo's enabled, and I used Automatix to install dvdrip.  I am guessing that the behavior is 'correct', however, because I have installed Dapper twice (32 bit, and 64 bit), and both times I ended up with only xvid4.

---

### Post by grendelkhan on 2006-06-09
What's the difference between xvid2 and xvidcore4?

---

### Post by rpesq on 2006-06-09
Per the DVD::RIP page...
> XviD variants
transcode support different versions of the XviD codec. Since transcode version 0.6.9 these are: xvid usually defaults to xvid2 (depends on your transcode installation), which is XviD 0.9. xvid3 is the current CVS HEAD of Xvid. xvid4 is the dev-api-4 branch, which will be released as XviD 1.0, once it's finished.

---

### Post by whatever on 2006-06-09
[QUOTE=rpesq]Per the DVD::RIP page...[/QUOTE]
xvid 1.1 is the current final release, so the text you are referring to was probably written some years ago :rolleyes: 

-> xvid4 is what you want

---

### Post by rpesq on 2006-06-09
With all due respect, this was explained in my original post:  > I need Xvid2 because it is the most compatible with my set-top dvd/divx player (Philips dvp-642). The other codecs do not work as well for my needs..  In fact, they do not work at all for my needs, and that includes xvid4.

Likewise, installing xvidcore1.1 from source does not supply xvid2.

---

### Post by rpesq on 2006-06-09
In case anyone else is looking for the solution, here is how I solved it.
After some educated guessing as to what file I needed, you can find xvidcore-0.9.2 from:
[http://downloads.xvid.org/downloads/xvidcore-0.9.2.tar.gz](http://downloads.xvid.org/downloads/xvidcore-0.9.2.tar.gz)

(There does not appear to be link to that file from the xvid download page, although the link works at this time.)

Make install like normal.  When done, the libxvidcore.so.2 and libxvidcore.so.2.1 files will be in the WRONG location.   They install into /usr/local/lib.   You need to copy them to /usr/lib.  You need to be root to do that.

If the xvid2 option in DVD::RIP still does not start when you press Transcode, then recreate the symlink by:
> $cd /usr/lib
$sudo ln -s libxvidcore.so.2.1 libxvidcore.so.2

---

### Post by qBaz on 2006-06-09
[QUOTE=rpesq]When done, the libxvidcore.so.2 and libxvidcore.so.2.1 files will be in the WRONG location.   They install into /usr/local/lib.   You need to copy them to /usr/lib.  You need to be root to do that.[/QUOTE]

Does it work if you edit /etc/ld.so.conf to include the line

 /usr/local/lib

and then run "sudo ldconfig"?  From your description, it sounds like the better long term solution is to tell ld where your libraries are instead of making alternate copies in /usr/bin.

Just a thought.

---

### Post by rpesq on 2006-06-09
Hi qBaz,

Sounds interesting.  I am still learning, so that does sound better. Interesting, though, is that I also installed the old divx 5 encoder files, and they installed into /usr/local/lib, but dvd::rip finds them without any problem.  I assume that dvd::rip knew that the divx files install themselves there, since that package is quite old.  But dvd:rip seems to want xvid,xvid2,xvid3,xvid4 to be in /usr/lib.

Next time I need do this, I'll try your suggestion.  I presume that your suggestion is similar to defining "path" back in the old msdos days?

---

### Post by qBaz on 2006-06-10
[QUOTE=rpesq]Interesting, though, is that I also installed the old divx 5 encoder files, and they installed into /usr/local/lib, but dvd::rip finds them without any problem.  [...]

Next time I need do this, I'll try your suggestion.  I presume that your suggestion is similar to defining "path" back in the old msdos days?[/QUOTE]

Well, kinda.  This analogy may or may not work, but think of the files in /usr/lib or /usr/local/lib as being cookbooks, full of recipes, and the directories themselves as specific bookshelves. A given program doesn't want to have to remember every recipe in the world, so it simply says that in order to run, it's going to want access to cookbook A and cookbook B.  When it runs, it uses certain recipes from each.

If it can't find a given cookbook, it can't run, and so it'll error out, either by checking around for the cookbook right up front and telling you it can't find it, or (less gracefully) by attempting to run, getting to the point where it needs a given recipe, failing to find it, and **then** telling you it's failed.

Adding things to ld.so.conf and running ldconfig is a way of telling most any program about what bookshelves contain cookbooks, i.e. where to go looking for the things they need.  (by this point, I'm starting to wonder whether this analogy is still any good, but I'm this far into it, so I might as well soldier on.)

Glad to hear dvd::rip is working for you now, though.  :)

---

