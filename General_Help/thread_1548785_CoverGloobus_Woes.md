---
title: "CoverGloobus Woes"
date: 2010-08-08
forum: General Help
---

### Post by N8-bit on 2010-08-08
I understand CoverGlobus is some pretty hacky python, but I really want this sucker properly installed. 

Now, I can run version 1.3 from the python source and it runs fine, with the exception of not being able to get the album artwork from Banshee.

However, after installing version 1.6, I get this error after trying to run it from the command line: (Have not attempted to run it straight from the python source, compilation using make fails with the current build.)
```

***********:~$ covergloobus
[WARNING] Using default Configuration
[INFO] UI: Theme: BadChoice
Traceback (most recent call last):
  File "/usr/share/covergloobus/covergloobus.py", line 531, in <module>
    sys.exit(cg.main())
  File "/usr/share/covergloobus/covergloobus.py", line 87, in main
    self.init() #Init configurations
  File "/usr/share/covergloobus/covergloobus.py", line 107, in init
    self.init_lyrics()
  File "/usr/share/covergloobus/covergloobus.py", line 173, in init_lyrics
    self.lyrics = LyricSearch(self.config)
  File "/usr/share/covergloobus/lyricsearch.py", line 53, in __init__
    self._load_engines()
  File "/usr/share/covergloobus/lyricsearch.py", line 63, in _load_engines
    exec "from " + name + " import *"
  File "<string>", line 1, in <module>
  File "/usr/share/covergloobus/lyrics/lyricsplugin.py", line 23, in <module>
    from common import GenericLyric
ImportError: cannot import name GenericLyric

```Am I missing some sort of python module, or am I simply trying to start up CoverGloobus incorrectly, or is there some other problem? :(

---

### Post by Rahmenlos on 2010-11-04
anyone has a solution for that? I'm stuck at the same error.

---

