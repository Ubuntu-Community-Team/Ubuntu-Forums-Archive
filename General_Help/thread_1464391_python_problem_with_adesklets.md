---
title: "python problem with adesklets"
date: 2010-04-28
forum: General Help
---

### Post by meral.ch on 2010-04-28
adesklets-scripts under ubuntu 10.4 do not work, I receive the following error:

```
test@x301:~/Downloads/Programs/CircleMeter$ python cpu_meter.py --nautilus
Traceback (most recent call last):
  File "cpu_meter.py", line 1, in <module>
    from circlemeter import *
  File "/home/test/Downloads/Programs/CircleMeter/circlemeter.py", line 2, in <module>
    from adesklets.commands import *
  File "/usr/lib/python2.6/dist-packages/adesklets/__init__.py", line 30, in <module>
    from adesklets.initializer import _Initializer
  File "/usr/lib/python2.6/dist-packages/adesklets/initializer.py", line 13, in <module>
    from children_handler import _Children_handler
  File "/usr/lib/python2.6/dist-packages/adesklets/children_handler.py", line 5, in <module>
    from signal_handler import Signal_handler
  File "/usr/lib/python2.6/dist-packages/adesklets/signal_handler.py", line 12, in <module>
    class Signal_handler:
  File "/usr/lib/python2.6/dist-packages/adesklets/signal_handler.py", line 20, in Signal_handler
    func = posix_signal.signal
AttributeError: 'module' object has no attribute 'signal'
```Architecture is AMD64.

Thank you for your consideration.

---

