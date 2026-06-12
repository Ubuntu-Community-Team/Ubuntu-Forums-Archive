---
title: "EnvyNG doesn't start"
date: 2010-03-08
forum: General Help
---

### Post by Antiverminseed on 2010-03-08
High i've been having a lot of problems with the ATI Catalyst 10.2-driver so i decided to try using EnvyNG instead. Now I installed it using apt-get install and it didn't show any error-messages but it won't start. I tried booting it from terminal with sudo envyng -t but it didn't suceed either. 

I'm I using the wrong command? Does anyone recognize this problem? 

When i type in sudo envyng -t in terminal i get this:

```
Traceback (most recent call last):
  File "interface.py", line 428, in <module>
    a = Interface()
  File "interface.py", line 126, in __init__
    self.abstract = abstraction.Abstraction(progress, True)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 35, in __init__
    self.hardware = detection.HardwareDetection()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 48, in __init__
    self.getCards()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 144, in getCards
    self.atiOrderedList = self.drivers['fglrx'].keys()
```

Could it be I have to remove my other driver before running envyng? If so, how do I do it?

I appreciate any kind of help!

---

