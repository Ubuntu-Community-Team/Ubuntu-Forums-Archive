---
title: "Synaptic Closed Unexpectedly"
date: 2010-11-05
forum: General Help
---

### Post by karmila on 2010-11-05
Hi, I have this problem; each time I go to synaptic and search for any packages, synaptic window instantly closed just after I type the second character. It seems failed on indexing or something. Here is the message when I ran it from terminal:

> me@me-desktop:~$ sudo synaptic
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
  File "/usr/share/software-center/softwarecenter/db/update.py", line 64, in <module>
    axi_values = parse_axi_values_file()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 43, in parse_axi_values_file
    (key, value) = line.split()
ValueError: need more than 1 value to unpack
Segmentation fault
me@me-desktop:~$ 

It happened after I did fsck to my root partition from fedora live cd. It founds many errors and attempted to fix it and I just 'yes' it all. I use fedora live cd because the cd was on my cd drive that time... heh

I did fsck because ubuntu won't boot after I hard reseted it before. I tried compiz experimental plugin and it freeze my Desktop and the console also.

---

### Post by blitzter47 on 2012-02-14
link in this forum : [http://ubuntuforums.org/showthread.php?t=1359893](http://ubuntuforums.org/showthread.php?t=1359893) may help for synaptic... And then reinstall all package named «python» may get rid of the error messages about files with .py extension.

---

