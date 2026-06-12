---
title: "Cannot install .deb files any more, software center doesn't start from main menu"
date: 2010-10-31
forum: General Help
---

### Post by Rumtscho on 2010-10-31
Yesterday, I made a clean install of 10.10 (64 bit). Among others, I installed World of Goo from a .deb file, and it worked fine. 

Today, I wanted to install Skype from the .deb file. When I double-click the file, I get a "wait" cursor for ~20 sec, then nothing happens. When I try to start Software Center from the Main menu, I also get the Wait cursor and then nothing happens. 

I started software-center from the terminal and the software center opened, despite some warnings in the terminal. I could install some random application from the list. Then I tried to start ```
sudo software-center ./skype-ubuntu.intrepid_2.1.0.81-1_amd64.deb
``` and the software center window showed, with Skype selected. When I clicked Install, there was an error message. Despite the "no such a file or directory" part, I am sure that the file name is correct (I tab-completed it). 

This is the error message I received when I tried to install: 
```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 841, in _simulate_helper
    self._cache)
  File "/usr/lib/python2.6/dist-packages/apt/debfile.py", line 57, in __init__
    self.open(filename)
  File "/usr/lib/python2.6/dist-packages/apt/debfile.py", line 66, in open
    self._debfile = apt_inst.DebFile(open(self.filename))
IOError: [Errno 2] No such file or directory: './skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb'

```

Here are the warnings I received when I started the software center: 
```
rumtscho@bradbury:~/Downloads$ sudo software-center ./skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb 
2010-10-31 19:40:38,149 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2010-10-31 19:40:38,149 - root - WARNING - failed to add sca db Couldn't detect type of database
2010-10-31 19:40:38,167 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2010-10-31 19:40:38,167 - root - WARNING - No styling hints for Raleigh were found... using Human hints.
2010-10-31 19:40:38,930 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2010-10-31 19:40:38,930 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/update.py', 367, '_error_cb')'
2010-10-31 19:40:38,930 - root - WARNING - error: Operation not supported
2010-10-31 19:40:40,408 - softwarecenter.app - INFO - software-center-agent finished with status 1
2010-10-31 19:40:51,206 - softwarecenter.backend - ERROR - error in _on_trans_finished 'Error: An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at http://launchpad.net/aptdaemon/+filebug and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 841, in _simulate_helper
    self._cache)
  File "/usr/lib/python2.6/dist-packages/apt/debfile.py", line 57, in __init__
    self.open(filename)
  File "/usr/lib/python2.6/dist-packages/apt/debfile.py", line 66, in open
    self._debfile = apt_inst.DebFile(open(self.filename))
IOError: [Errno 2] No such file or directory: './skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb'
'


```

---

### Post by oldos2er on 2010-10-31
Did you try ```
sudo dpkg -i skype-ubuntu.intrepid_2.1.0.81-1_amd64.deb
```

---

### Post by ajgreeny on 2010-10-31
I don't know if, nor why, it might make any difference, but try installing **gdebi** first, and then try right clicking on the skype .deb file and choosing open with gdebi.  It may help as gdebi will automatically download any missing dependencies.

For some reason gdebi is not installed by default in maverick, which I think is a bit of a shame.  It is still available in the repos, however.

---

### Post by scouser73 on 2010-10-31
> **ajgreeny said:**
> I don't know if, nor why, it might make any difference, but try installing **gdebi** first, and then try right clicking on the skype .deb file and choosing open with gdebi.  It may help as gdebi will automatically download any missing dependencies.

For some reason gdebi is not installed by default in maverick, which I think is a bit of a shame.  It is still available in the repos, however.

+1 for this.

---

### Post by Rumtscho on 2010-10-31
> **ajgreeny said:**
> installing **gdebi** first, and then try right clicking on the skype .deb file and choosing open with gdebi. 

Thank you, that worked - meaning that I can use it as a workaround for installing .deb files. I would still appreciate ideas for turning the software center back on. I don't use it much, but it is a shame for a new OS to break irreparably on the second day :(

---

### Post by ajgreeny on 2010-10-31
Sorry, but I can't really help with that; I never use the ubuntu Software Center, always synaptic for me!

---

