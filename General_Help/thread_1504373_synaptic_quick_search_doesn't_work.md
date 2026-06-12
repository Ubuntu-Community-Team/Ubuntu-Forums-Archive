---
title: "synaptic quick search doesn't work"
date: 2010-06-07
forum: General Help
---

### Post by JBA2337 on 2010-06-07
I just upgraded my computer to Ubuntu 10.04 Lucid. Whenever I open Synaptic Package Manager it opens normally. If I type into the "Quick search" box, when I try to type in a word as soon as I type the second letter Synaptic immediately closes. However, if I click on the full "Search" button, this function works as it should. I just can't use Quick Search. Synaptic closes every time.

I uninstalled synaptic from a terminal by typing [CODE] apt-get remove synaptic. Then I reinstalled using [CODE] apt-get install synaptic. Reinstalling did not fix the problem.

Does anyone have an idea how to fix this?

Thanks!

JBA2337

---

### Post by gandra on 2010-06-07
Hi !
 
Sorry to ask in wrong place ...
 
How can I post a thread in the forum ?/
 
Were is the icon that allows I type the thread ?
 
Thanks
 
Gandra

---

### Post by dcstar on 2010-06-08
> **JBA2337 said:**
> I just upgraded my computer to Ubuntu 10.04 Lucid. Whenever I open Synaptic Package Manager it opens normally. If I type into the "Quick search" box, when I try to type in a word as soon as I type the second letter Synaptic immediately closes. However, if I click on the full "Search" button, this function works as it should. I just can't use Quick Search. Synaptic closes every time.

I uninstalled synaptic from a terminal by typing ```
 apt-get remove synaptic. Then I reinstalled using [CODE] apt-get install synaptic. Reinstalling did not fix the problem.

Does anyone have an idea how to fix this?

Thanks!

JBA2337

Try:

[CODE]sudo update-apt-xapian-index -f -v
```

---

### Post by JBA2337 on 2010-06-08
To dcstar:

Thanks for your suggestion, I tried it.

In a terminal I typed [CODE] sudo update-apt-xapian-index -f -v

It did not work. Still when I type in two letters in the Synaptic Quick Search box, Synaptic shuts down.

jba2337

---

### Post by JBA2337 on 2010-07-03
Somehow this problem fixed itself. Synaptic Quick Search now works.

JBA2337

---

### Post by loukingjr on 2010-10-22
> **dcstar said:**
> Try:

```
sudo update-apt-xapian-index -f -v
```

I'm having the same issue with a new install of Ubuntu Tutik Remix 10.10 DVD. I tried the command mentioned but didn't seem to help. Plus, when I ran it I get these error messages...

(update-apt-xapian-index:6359): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(update-apt-xapian-index:6359): atk-bridge-WARNING **: IOR not set.

(update-apt-xapian-index:6359): atk-bridge-WARNING **: Could not locate registry
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 97, in <module>
    if not indexer.setupIndexing(force=opts.force):
  File "/usr/lib/pymodules/python2.6/axi/indexer.py", line 441, in setupIndexing
    self.readPlugins(langs=self.langs, progress=self.progress)
  File "/usr/lib/pymodules/python2.6/axi/indexer.py", line 423, in readPlugins
    addon = Addon(fullname, **kw)
  File "/usr/lib/pymodules/python2.6/axi/indexer.py", line 49, in __init__
    self.module = imp.load_source("axi.plugin_" + self.name, fname)
  File "/usr/share/apt-xapian-index/plugins/software-center.py", line 10, in <module>
    from softwarecenter.db.update import *
  File "/usr/share/software-center/softwarecenter/db/update.py", line 70, in <module>
    cataloged_times = cPickle.load(open(CF))
EOFError

any thoughts?
thanks

---

