---
title: "server cannot read .php strings"
date: 2010-03-24
forum: General Help
---

### Post by dayobiz on 2010-03-24
localhost is now fine and localhost/test.php too. However php embedded in html files refused to save in /var/www? what is wrong with my server not being able to read .php strings?

---

### Post by kamaji792 on 2010-03-24
Hi Dude,

Not sure I entirely understand your problem.

You talk about embedding PHP in an HTML file.  Do you mean you are using **<?php... ...?>** in a file with an ***.html** extension?  If you are it will not work.  The file needs to have a ***.php** extenstion.

Or are you having problems saving files in the /var/www directory.  This is most likely to be a permissions issue, but as you have **localhost/test.php** working it suggests you are able to write to /var/www.

All the best

---

### Post by dayobiz on 2010-03-24
hey,thanks. the problem was permission issue, i later got to know i had to login as root.

---

