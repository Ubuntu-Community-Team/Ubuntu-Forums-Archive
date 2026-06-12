---
title: "yaehmop huckle chemistry program install"
date: 2009-07-29
forum: General Help
---

### Post by conradin on 2009-07-29
Hi all, 
I am trying to install a program called yaehmop.
Available from:
[http://sourceforge.net/projects/yaehmop/files/yaehmop-all/3.0.3/yaehmop.3.0.3.src.tar.gz/download](http://sourceforge.net/projects/yaehmop/files/yaehmop-all/3.0.3/yaehmop.3.0.3.src.tar.gz/download)
I'm not sure how to install it though. I dont see any enlightening readMe files in any of the directories. Can I get some help here? I'm using jaunty.

---

### Post by michy99 on 2009-07-29
I ran across this on the net:

Suppose you extracted yaehmop into the directory ~/yaehmop,
look in that directory to see if there is a directory named bin, if not,
create it like this:
> mkdir ~/yaehmop/bin
you now ought to be able to compile and install everything like this:
> cd ~/yaehmop/tightbind
> make -f makefile.linux install
> cd ~/yaehmop/viewkel
> make -f makefile.linux install

This is from this site:

[http://sourceforge.net/mailarchive/forum.php?thread_name=BAY106-F204F95540B7FA1738AB3E3DF5D0%40phx.gbl&forum_name=yaehmop-help](http://sourceforge.net/mailarchive/forum.php?thread_name=BAY106-F204F95540B7FA1738AB3E3DF5D0%40phx.gbl&forum_name=yaehmop-help)

---

