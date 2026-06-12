---
title: "checking memory status"
date: 2010-07-28
forum: General Help
---

### Post by ksihawk7 on 2010-07-28
When checking memory status by using the command free -m,is the top part the part that shows how much space is being used and how much is free? Also, what is this in? Megabytes or gigabytes?

---

### Post by Deiz on 2010-07-28
Check out man free.

The -m flag outputs sizes in megabytes. You could use -g for gigabytes, but be warned that it only prints integers - Which is to say, 1.9 GB of usage will be rounded down to 1 GB.

The top row are the true usage values, but the second line is probably what you actually want. Linux caches files in memory that isn't being used by other programs - So even though the top row reports a very small amount is free, in actual fact all the space used to cache files will be immediately given to new programs if they request it.

Give [this](http://www.linuxatemyram.com/) a read if you're interested in learning a bit more.

---

