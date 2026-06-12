---
title: "Share LAMP webpage files across servers via symlinks &amp; dropbox?"
date: 2012-03-11
forum: General Help
---

### Post by cdaringe on 2012-03-11
Hi all:

I have my server files stored in

/home/cdaringe/Dropbox/project/repchill

As usual, web root ~ /var/www/

I want to pull up any of my machines to be able to work on the files directly in my dropbox, all while being able to browse to localhost on each machine and have the server query the appropriate files

if i remove the www dir from /var, then create a symlink 'ln -s ...repchill www', it kills apache and i can't restore it from a 403 forbidden error.

Any advice on how to best accomplish this would be great!

Thanks!

-Chris

---

