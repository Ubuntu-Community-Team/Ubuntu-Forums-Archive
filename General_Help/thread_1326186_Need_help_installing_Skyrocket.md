---
title: "Need help installing Skyrocket"
date: 2009-11-14
forum: General Help
---

### Post by dougalkerr on 2009-11-14
Yes I suppose I am not alone... 9.10 doesn't have Skyrocket screensaver on it's list - WHY??? I agree with other comments that it is possibly one of the best SS around.
I downloaded the file and with help already from here I now have the getopt after installing the gnulib package (a little slip-up from the Skyrocket file producer here, surely the program should hunt down and install all files required - oh well).
Now I tried to configure, make and install again and get this last couple of lines;

'checking for C++ compiler default output... configure: error: C++ compiler cannot create executables
See `config.log' for more details.'

What should I do next?

Thanks again for everyones help with everything, just shows how people from around the world are more than willing to help one another.

---

### Post by Jehubuntoo on 2009-12-18
Its a little late but I found your post.  Try this:

sudo apt-get install xscreensaver-data-extra

---

### Post by mdlueck on 2009-12-20
Actually the package "rss-glx" is where Skyrocket resides.

Correct, that package is not installed in 9.10 by default.

---

