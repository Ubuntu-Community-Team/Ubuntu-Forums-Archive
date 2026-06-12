---
title: "Help restoring a site from a Duplicity backup"
date: 2010-11-29
forum: General Help
---

### Post by tarahmarie on 2010-11-29
Hi, all!

NS, my good friend and chief backend coder died last week. He was hosting my site, which consists of a lamp stack built on buntu server edition.

So, in addition to missing my friend, my business site is down.  I categorically refuse to let this thing defeat me; I am a front end dev, but I can figure it out--with a little help from my Buntu buddies ;-)

(1) I have created a full web server after purchasing cloud server space. I made a lamp stack, created the user, installed drupal 6, set some permissions, etc--not necessarily in that order. WHEW. That was somewhat terrifying. I pointed one of my spare domain names through my DNS account at my site's IP, and got the Yay! message showing that I'd set the site up properly. You may now all feel free to pat me on the head and say "GOOD front end dev!"

(2) Here's my deal: I have a full Duplicity backup stored at AWS; a big file and maybe 40 diff tarballs from backups. I at least had the good sense to make my dev do nightlys. How do I go from the files I have to putting Humpty Dumpty back together again? I've installed Duplicity on my web server; how do I combine all the backup files, put them in the file structure of the server I've created, and boot the whole damn thing up?

I'm grateful for all help; I've gone as far as I can on my own, and I don't even know how to restore the SQL db with the data.  Does anyone have a place for me to start?

---

