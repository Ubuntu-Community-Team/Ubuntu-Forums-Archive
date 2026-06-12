---
title: "mod_python Pain"
date: 2009-08-25
forum: General Help
---

### Post by dumah_uk on 2009-08-25
I have an Ubuntu Server (8.04) which I want to use to host a django site. The site was developed using python2.6 and I wanted to continue using it without messing up the system version of python which is python2.5.

So...I build a version of python2.6 in its own directory and dont update the symlinks for the normal system installed python. I create a link for "python2.6" and use this to install all the python libs I need using "python2.6 setup.py install --prefix=/my/python/installation/path". This works fine and testing python2.6 I have access to import all the libs I need

All this works well until I need to install mod_python. As I have a specific version of python I need, I use "./configure --with-python=/my/python/installation/path/bin/python2.6" followed by make and make install to build mod_python. This is fine until I try to load the module in apache2.

I add the "LoadModule python_module /usr/lib/apache2/modules/mod_python.so" line to apache2.conf and try to restart the server.

The error I get is  **** Starting web server apache2 apache2: Syntax error on line 184 of /etc/apache2/apache2.conf: Cannot load /usr/lib/apache2/modules/mod_python.so into server: /usr/lib/apache2/modules/mod_python.so: undefined symbol: floor***

I've tried googling and I'm now completely stuck

Please...help...me!

---

### Post by dumah_uk on 2009-08-25
I think I fixed it. Here's the solution (at least what I hope is the solution) for other users:

Look at reply 4 on [http://code.google.com/p/modwsgi/issues/detail?id=115](http://code.google.com/p/modwsgi/issues/detail?id=115)

It looks like there's a library missing from the mod_python configure process. I ran configure, then went to the Makefile in the src directory and added "-lm" to the "LDLIBS" symbol. A quick "make clean, make, make install" updated the mod_python library and now apache2 starts.

Fingers crossed, that hopefully fixed it

---

