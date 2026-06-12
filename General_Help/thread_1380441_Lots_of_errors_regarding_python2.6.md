---
title: "Lots of errors regarding python2.6"
date: 2010-01-13
forum: General Help
---

### Post by Jarige on 2010-01-13
When executing different programs varying from the Ubuntu Software Manager to pstotxt and lots of other programs I get tons of errors that have to do with Python2.6, whatever it is. I think it got corrupted since my netbook turned of while installing some (Dutch) language packs.
The smaller problem, is that the language packs failed to install properly, and I can see some Dutch sentences between the English ones sometimes...
The major prolem, is that somehow a lot of programs won't work anymore, mainly terminal programs. pstotxt is one of any examples. Installing software doesn't always work because of these errors.

This is the output when I want to use pstotxt to convert a .pdf to .txt file:

```

Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 8, in <module>
    import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 5, in <module>
    from util import gettext_wrapper as _
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 35, in <module>
    _ = gettext_wrapper = setup_locale()
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 28, in setup_locale
    gettext.install("command-not-found", unicode=True)
  File "/usr/lib/python2.6/gettext.py", line 508, in install
    t = translation(domain, localedir, fallback=True, codeset=codeset)
  File "/usr/lib/python2.6/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.6/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.6/gettext.py", line 273, in _parse
    magic = unpack('<I', buf[:4])[0]
struct.error: unpack requires a string argument of length 4


```

Can anyone solve this?

Would be greatly appreciated :D

---

### Post by Jarige on 2010-01-17
BUMP. I still can't install a lot of programs, but when I wan't to uninstall python2.6 it will remove a lot of programs that depend on it. Including Firefox, OpenOffice.org etc. It will take a long time to install them again and I don't want to do that...
Is there any command which will force a reinstall without deleting the packages that depend on it?

---

### Post by oldfred on 2010-01-17
You do not want to uninstall python2.6, more than likely you will have to reinstall as many parts of ubuntu rely on it.

In synaptic select python and choose reinstall.

from the command line:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install --reinstall python2.6

---

### Post by Jarige on 2010-01-17
Thanks :)
I've found the solution just moments before you suggested the same solution. I'm very grateful anyway :) Thanks for replying, many people watched but didn't reply. You did :)

Thanks :D

---

