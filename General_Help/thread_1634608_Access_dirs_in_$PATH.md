---
title: "Access dirs in $PATH"
date: 2010-11-30
forum: General Help
---

### Post by shadow_code on 2010-11-30
Hi, does anyone know if it's possible to access a directory that is in the $PATH env var? Note: I'm talking about accessing a dir via the PATH (not adding the dir to the PATH).

e.g.

PATH=/usr/bin

File is in: /usr/bin/dir/script

Then access the script via something like:
dir/script (from anywhere)

cheers :)

---

### Post by Liverbones on 2010-11-30
As far as I know, that's pretty incongruous with how things work on a Linux filesystem. Trying to run dir/script is interpreted as trying to run a script from a directory within the current directory, so it's essentially equivalent to ./dir/script. There are just... innumerable problems with that idea. But honestly, I've never tried, and you never know... it could certainly be possible. I just fail to see how it would be particularly useful, or desirable, even.

There are just too many things that could go wrong.

---

