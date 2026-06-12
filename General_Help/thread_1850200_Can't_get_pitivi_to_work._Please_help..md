---
title: "Can't get pitivi to work. Please help."
date: 2011-09-26
forum: General Help
---

### Post by BlackoutWorm on 2011-09-26
Hey. I installed pitivi now because openshot's new version doesn't work for me, so I had to try something else.
Anyway, here's what the terminal says when I try to debug it from there:

Traceback (most recent call last):
  File "/usr/bin/pitivi", line 132, in <module>
    _run_pitivi()
  File "/usr/bin/pitivi", line 127, in _run_pitivi
    sys.exit(ptv.main(sys.argv))
  File "/usr/lib/pitivi/python/pitivi/application.py", line 531, in main
    ptv = StartupWizardGuiPitivi(debug=options.debug)
  File "/usr/lib/pitivi/python/pitivi/application.py", line 382, in __init__
    FullGuiPitivi.__init__(self, debug)
  File "/usr/lib/pitivi/python/pitivi/application.py", line 275, in __init__
    InteractivePitivi.__init__(self, debug)
  File "/usr/lib/pitivi/python/pitivi/application.py", line 223, in __init__
    Pitivi.__init__(self)
  File "/usr/lib/pitivi/python/pitivi/application.py", line 135, in __init__
    self.effects = EffectsHandler()
  File "/usr/lib/pitivi/python/pitivi/effects.py", line 123, in __init__
    self._setAllEffects()
  File "/usr/lib/pitivi/python/pitivi/effects.py", line 141, in _setAllEffects
    added = self.addStreams(element_factory, effect)
  File "/usr/lib/pitivi/python/pitivi/effects.py", line 192, in addStreams
    stream = get_stream_for_pad(pad)
  File "/usr/lib/pitivi/python/pitivi/stream.py", line 362, in get_stream_for_pad
    stream.pad_id = pad_id
AttributeError: 'NoneType' object has no attribute 'pad_id'

Can someone help me plz?

---

### Post by BlackoutWorm on 2011-09-26
bump. any solution?

---

### Post by BlackoutWorm on 2011-09-28
**[color="magenta"][size="4"]bump[/size][/color]**

---

### Post by BlackoutWorm on 2011-10-01
[size="4"]**[color="lime"]bump[/color]**[/size]

---

### Post by nuunkotad on 2011-10-04
here can't get pitivi to render any movie - "Render project" button inactive.
please help if someone have any solution for this.

[SIZE="2"]

what a shame. must add to timeline to get render. xO[/SIZE]

---

### Post by colobix on 2011-12-07
Same here.
But I can't even get the program to start.
Please help.

---

