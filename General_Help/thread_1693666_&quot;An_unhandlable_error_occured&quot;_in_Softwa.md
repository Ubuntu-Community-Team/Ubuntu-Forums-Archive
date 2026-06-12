---
title: "&quot;An unhandlable error occured&quot; in Software Center"
date: 2011-02-23
forum: General Help
---

### Post by a4rithm5)kal.rhythms on 2011-02-23
The message reads

[B]An unhandlable error occured
[/B]
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

[B]Details:

[/B]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I have been a pc user most of my life so I'm new to the linux systems. Please help ](*,)

---

### Post by oldos2er on 2011-02-23
Can you open a terminal (Applications, Accessories, Terminal), run this command and if there are errors, please post all the output here? ```
sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by pinak.nubs on 2011-05-09
i ran your command and now i am missing the minimise, maximise, close buttons?????

---

### Post by oldos2er on 2011-05-09
It would probably be a good idea for you to start a new thread. Be sure to mention which version of Ubuntu you're using, which desktop environment, and any other details about your problem.

---

