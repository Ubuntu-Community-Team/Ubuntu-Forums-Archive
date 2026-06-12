---
title: "kcachegrind installation not working"
date: 2012-07-16
forum: General Help
---

### Post by dragonfly41 on 2012-07-16
I'm still using ubuntu 10.10 for development.

I've got XDebug + PHP5 working together.   
Trace output is placed in trace directory.

Now I'm trying to install kcachegrind to inspect cachegrind output.

sudo apt-get install kcachegrind

According to this

[http://solutionfactor.net/blog/2010/12/21/ubuntu-10-10-installing-xdebug-and-kcachegrind-with-php-5/](http://solutionfactor.net/blog/2010/12/21/ubuntu-10-10-installing-xdebug-and-kcachegrind-with-php-5/)

it should be seen in Applications > Programming > KCacheGrind

but there is no sign of KCacheGrind

Any ideas on installing kcachegrind to launch point?

When I look in Synaptic Package Manager these packages are marked as installed ..

kcachegrind 4:4.5.5-0ubuntu2
kcachegrind-convertors 4:4.5.5-0ubuntu2

===============================================

[EDIT]

I later found that I can right click on a callgrind.out file and "open with KCacheGrind"
to inspect cachegrind.

I have a variable in php.ini which is
xdebug.profiler_output_name = "callgrind.out.%R"

but I haven't yet found the link to open KCacheGrind directly as an application.

If I right click on Applications > Edit Menus > Programming
I can see that KCacheGrind is ticked and I can read its properties.
Perhaps it will show up in Application menu when I reboot ubuntu.

===============================================

[EDIT]

After trying to launch kcachegrind in terminal the GUI launched

and the Kcachegrind link now appears under Applications  > Programming

I'm now integrating with Komodo Free Editor as IDE.

---

