---
title: "error starting wiithon"
date: 2011-01-09
forum: General Help
---

### Post by davidtuti on 2011-01-09
Hi,
Recently I've installed wiithon but when I execute the program I dont see any windows.
When I try from command-line:
```

david@david-linux:~$ wiithon
Traceback (most recent call last):
  File "/usr/games/wiithon", line 138, in <module>
    App()
  File "/usr/games/wiithon", line 49, in App
    util.configurarLenguaje(prefs.APPLICATION_LANGUAGE)
  File "/usr/share/wiithon/util.py", line 525, in configurarLenguaje
    setLanguage(inicial)
  File "/usr/share/wiithon/util.py", line 491, in setLanguage
    lang = gettext.translation(config.APP, languages=[locale])
  File "/usr/lib/python2.6/gettext.py", line 484, in translation
    raise IOError(ENOENT, 'No translation file found for domain', domain)
IOError: [Errno 2] No translation file found for domain: 'wiithon'

```

Any help?
Many thanks and sorry for my english!

---

### Post by keroman on 2011-01-16
try here, worked for me
[https://bugs.launchpad.net/wiithon](https://bugs.launchpad.net/wiithon)

---

