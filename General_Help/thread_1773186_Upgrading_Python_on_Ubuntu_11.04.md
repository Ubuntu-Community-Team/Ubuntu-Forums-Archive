---
title: "Upgrading Python on Ubuntu 11.04"
date: 2011-06-01
forum: General Help
---

### Post by airspoon on 2011-06-01
Hello, I'm new to Ubuntu (11.04) and I'm wanting to upgrade Python. According to the "python" command in the terminal, I'm running Python 2.7. However, I'm looking at installing IDLE and I see that there is a Python 3.2. I'm assuming then, that I have an older version of Python given that I have 2.7. 

I went to Synaptic and I see Python 2.7, but I don't see Python 3.2. However, I do see Python 3.2 documentation and other packages seemingly related to Python 3.x.

Is Python 2.7 more stable or better and if not, how do I upgrade my version of Python? I did a search for this topic and I only found an older thread on it (2007, I think) so I'm not sure how relevant the information still is. 

Any help would be greatly appreciated.

---

### Post by oldfred on 2011-06-01
Whatever you do, do not uninstall python2.7. Older versions of Ubuntu totally stopped working including Internet without the installed version of python. Either chroot or total reinstall was then the only fix.

If you have installed python 3.x, then you can just run it if you want. You normally specify python3.x on command to load. When I edit my python files I change this to 3.1 when before it was just python.

#!/usr/bin/python3.1
# -*- coding: utf-8 -*-

Most of the small scripts i have downloaded from sites work with either 2.7 or 3.x except for print which then has to be print().

---

### Post by airspoon on 2011-06-01
Thank you, I was unaware that you could install two different versions of Python on one system. I'll certainly keep 2.7. 

As far as 3.2, do you know if those are in the Ubuntu repositories? Can I get it through apt-get, as I couldn;t find it in Synaptic, though I saw the Python 3.2 docs. Would it come with IDLE for 3.2?

Thanks.

---

### Post by oldfred on 2011-06-01
I am still in Maverick most of the time.

When I look in /usr/bin I see python, 2.6, 3 and 3.1. The python3 is just a link to my python 3.1. The python is a link to 2.6 in my Maverick. 

I have not installed any additional apts in Natty yet. My Natty just has python linked to python2.7.

What do you have in /usr/bin?

---

### Post by katykat on 2011-06-02
Meerkat has 2.6 and 3.1 in /usr/bin (I may need to update!)
Fedora 14 has 2.7 and 3.1 in /usr/bin

There have been no conflicts in either system. 

However... In Jaunty there was a never ending series of problems with it getting the two mixed up.

The two versions are not compatible with each other, and rightly 3.x should have been renamed to something else, like boa. 

And... whatever you do, dont even think of upgrading that horrid Perl 5.10 (5.12 is much better). 
It will mess up Perl and make the system unbootable.

---

