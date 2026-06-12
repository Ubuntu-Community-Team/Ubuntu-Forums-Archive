---
title: "Bibus gone hay-wire: please help restore"
date: 2006-04-19
forum: General Help
---

### Post by shuttleworthwannabe on 2006-04-19
I just used automatix to upgrade OOo to 2.0.1 from 1.9.125 (breezy deafult version).

Here is what I did to mess this whole up;
I had version 1.9.XX of OOo when I did the following
1. I added the bibus sources to the sources.list
2. installed the bibus 1.2 using synaptic, all the dependencies were added automatically
3. But when I fired bibus it would not allow me to activate the OOo_pipe for listening mode

So I decided to upgrade the OOo to 2.0.1 using automatix, but still i have the same problem:
I have pasted the secreen shot to illustrate the errors.

How do I rectify this so that I can use Bibus in OOo 2.0.1?
here is the trace back:```
** (python:17372): WARNING **: IPP request failed with status 1030
Traceback (most recent call last):
  File "/usr/bin/bibus", line 142, in ?
    bibframe1 = BibFrame.BibFrame(None, -1, BIB.TITLE)
  File "/usr/share/bibus/BibFrame.py", line 31, in __init__
    self.__loadConnectionModule()
  File "/usr/share/bibus/BibFrame.py", line 1480, in __loadConnectionModule
    import OOo
  File "/usr/share/bibus/OOo.py", line 54, in ?
    from bibOOo.bibOOoPlus import *
  File "/usr/share/bibus/bibOOo/bibOOoPlus.py", line 22, in ?
    from bibOOo.bibOOoBase import *
  File "/usr/share/bibus/bibOOo/bibOOoBase.py", line 24, in ?
    import uno
  File "/usr/lib/python2.4/site-packages/uno.py", line 37, in ?
    import pyuno
SystemError: dynamic module not initialized properly

```
Thanks in advance

PS: I was not sure if I posted in the right place. there is a duplicate thread under tips and tricks as well. So forgive me if I have violated some rules here.

---

### Post by shuttleworthwannabe on 2006-04-19
Thanks I managed to get it working. see this thread: [http://www.ubuntuforums.org/showthread.php?t=122841&page=6](http://www.ubuntuforums.org/showthread.php?t=122841&page=6)

---

