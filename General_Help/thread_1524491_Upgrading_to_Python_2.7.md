---
title: "Upgrading to Python 2.7"
date: 2010-07-05
forum: General Help
---

### Post by glastonbury on 2010-07-05
Python 2.7 is out. Would this be an upgrade that Canonical would push out via Update Manager or something I have to manually get?

I looked in Synaptic, and if I were to uninstall Python 2.6.5 to do a manual install of 2.7, Synaptic is saying it wants to uninstall a whole load of software, from Firefox to a ton of other things. Not sure I want to go that way. 

Thoughts?

---

### Post by oldfred on 2010-07-05
Whatever you do, do not uninstall 2.6. Your entire system runs on that and as you saw it will uninstall much of your system.

I have seen where others have installed python3 in parallel to run it also. I am sure you can do that. I would not expect Ubuntu would change to 2.7 until it was fully tested and then only as part of the next or later release cycle.

---

### Post by glastonbury on 2010-07-05
Thanks -- that's what I suspected, and it is one of the things that I am finding frustrating about Ubuntu. I have to wait until Canonical decides to include it before I can use it.

---

### Post by oldfred on 2010-07-05
There is nothing preventing you from using it. Many are creating programs and using python3. It just is not the standard install. You can install python2.7 but be sure not to overwrite the 2.6 install and create issues.

---

### Post by MCVenom on 2010-07-05
> **glastonbury said:**
> Thanks -- that's what I suspected, and it is one of the things that I am finding frustrating about Ubuntu. I have to wait until Canonical decides to include it before I can use it.
You can install it with no problem; I have Python 3.1 installed from the repos right now. You just can't uninstall the old Python; it'll break everything in Ubuntu that has it listed as a dependency.

I can understand wanting a specific version of Python for programming and development and whatnot, but why do you need to uninstall Python 2.6? :|

P.S.: To answer your original question, no, Py2.7 won't be pushed out through the Update Manager or added to the repos until Maverick; you'll have to find a *.deb package for it online or compile it yourself. I think you'll be glad to hear about Maverick's new 'Extras' repo though ;) - [http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html](http://www.webupd8.org/2010/06/new-post-release-repository-for-new.html)

---

### Post by srid on 2010-07-15
You can also install ActivePython 2.7 from here:
[http://www.activestate.com/activepython/downloads](http://www.activestate.com/activepython/downloads)

By default it installs into /opt/ActivePython-2.7/

After that, run "[FONT="Courier New"]/opt/ActivePython-2.7/bin/pypm install ipython readline[/FONT]" for a decent interactive shell. Then use the same [pypm]("http://pypm.activestate.com/") command to install other Python packages.

---

