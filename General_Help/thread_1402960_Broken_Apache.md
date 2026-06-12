---
title: "Broken Apache"
date: 2010-02-09
forum: General Help
---

### Post by Nonno Bassotto on 2010-02-09
I've been always using Apache. Yesterday a package I installed had the server thttpd as a dependency, and I installed it figuring it would not interfere with my existent Apache install (well, unless I ran the two simultaneously).

Now my Apache is not working anymore as expected, even after I removed (purged) thttpd. First, when I go to 127.0.0.1 I see the directory listing of /var/www, which is ok, but with the thttpd theme, which is strange. Here it is actually Apache running, I can check it by stopping Apache.

More worrying is the fact that not all site pages work as expected. Sometimes I get the PHP source or the directory listing, where my site was supposed to show.

This does not seem to happen if I use localhost instead of 127.0.0.1, but I cannot tell for sure if everything is really working. Any ideas?

---

### Post by Nonno Bassotto on 2010-02-09
Ok, I reinstalled everything Apache-related and now everything works. :D

---

