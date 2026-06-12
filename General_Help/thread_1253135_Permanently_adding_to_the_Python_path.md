---
title: "Permanently adding to the Python path"
date: 2009-08-29
forum: General Help
---

### Post by sccolbert on 2009-08-29
Ok, so I want some of my home built packages to overshadow the system packages. Namely, I have been numpy 1.3.0 from source with atlas support, and I need it to overshadow the system numpy 1.2.1 which I had to drag along as a dependency for other stuff. I have numpy 1.3.0 installed into /usr/local/lib/python2.6/dist-packages. The issue is that this directory is added to the path after the /usr/lib system paths. So python doesnt see my version of numpy. 

I have been combating this with a line in my .bashrc file:

export PYTHONPATH=/usr/local/lib/python2.6/dist-packages 

So when I start python from the shell, everything works fine. 

Problem show up when python is not executed from the shell, and thus the path variable is never exported. This can occur when I have launcher in the gnome panel or i'm executing from within wingide. 

So, how do I fix this so the local dist-packages is added to sys.path before the system directory ALWAYS? I can do this by editing site.py but I think it's kind of bad form to do it this way. 

Any ideas?

Cheers, 

Chris

---

