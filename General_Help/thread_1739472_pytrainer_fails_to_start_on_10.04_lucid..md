---
title: "pytrainer fails to start on 10.04 lucid."
date: 2011-04-26
forum: General Help
---

### Post by ravinderw on 2011-04-26
Hello All,

I'm thinking about getting a garmin 305 forerunner and had read that pytrainer was a good piece of software to use with it.

I wanted to have a look at it so installed pytrainer and tried to start it and it didn't. I tried to start it from a terminal and I got..

location: /usr/lib/xulrunner-1.9.2.16/libxpcom.so 
GTKEmbedGlueStartup failed
Traceback (most recent call last):
  File "/usr/bin/pytr", line 39, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/lib/pymodules/python2.6/pytrainer/main.py", line 48, in <module>
    from extensions.googlemaps import Googlemaps
  File "/usr/lib/pymodules/python2.6/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
SystemError: dynamic module not initialized properly


Does anyone have any ideas on how to get this working?

I'm a beginner using Ubuntu, so any help would be appreciated.

Thanks.

---

