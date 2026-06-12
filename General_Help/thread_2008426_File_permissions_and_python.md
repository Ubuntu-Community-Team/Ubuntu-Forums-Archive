---
title: "File permissions and python"
date: 2012-06-22
forum: General Help
---

### Post by Robing Goodfellow on 2012-06-22
Okay, I can't get this one figured out on my own, need a little help.

I have festival tts installed, proper path etc, (I can call it up in terminal by just typing festival) and it works fine.  Now I want to call it from a python program I'm working on.  I found a nifty little script called PyFest that allows me to do just that.  Downloaded PyFest, extracted it, tested it, it also works quite nicely as long as I'm in its directory.  I used the install file that comes with but I can't quite figure out how to fiddle with the permissions so that everything works nicely together.

When I do 
```

python setup.py install

```

I'm told I don't have permission.

I have moved the PyFest file out of Downloads and into /usr/local/lib/python2.7/dist_packages which is where the error message said the permission problem occurred, but I still don't have permission.

Is this a simple chmod?  Before running the python script? Or am I missing the bigger picture here?

Running precise on a 64 bit G62.

regards, Richard

---

### Post by steeldriver on 2012-06-23
well I imagine if you are trying to have it install stuff to a system directory you will need sudo

```
sudo python setup.py install
```

---

