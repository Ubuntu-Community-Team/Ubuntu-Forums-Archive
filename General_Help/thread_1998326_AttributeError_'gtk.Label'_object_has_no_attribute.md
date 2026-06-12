---
title: "AttributeError: 'gtk.Label' object has no attribute 'set_tooltip_text'"
date: 2012-06-06
forum: General Help
---

### Post by bkama1 on 2012-06-06
WHAT IS THIS.

```

Traceback (most recent call last):
  File "/usr/local/bin/oof2", line 38, in <module>
    oof.run()
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/oof.py", line 641, in run
    front_end(no_interp)  # all non-parallel menu items are executed here.
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/oof.py", line 365, in front_end
    import ooflib.common.IO.GUI.initialize
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/initialize.py", line 33, in <module>
    import ooflib.common.IO.GUI.oofGUI
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/oofGUI.py", line 370, in <module>
    gui = oofGUI()
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/oofGUI.py", line 83, in __init__
    accelgroup=accelgrp)
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/gfxmenu.py", line 71, in gtkOOFMenuBar
    item.construct_gui(menu, bar, accelgroup)
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/gfxmenu.py", line 165, in _OOFMenuItem_construct_gui
    new_gtkitem.add(self.gtklabel(new_gtkitem))
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/gfxmenu.py", line 137, in _gtklabel
    tooltips.set_tooltip_text(label,self.helpstr)
  File "/usr/local/lib/python2.7/site-packages/oof2/ooflib/common/IO/GUI/tooltips.py", line 30, in set_tooltip_text
    widget.set_tooltip_text(text)
AttributeError: 'gtk.Label' object has no attribute 'set_tooltip_text'


```

Newbie here. Been trying to resolve some issues with running this program(OOF2), after getting rid of some other errors, I now get this.

I see the error has to do with gtk, but reinstalling gtk hasn't done anything to fix it. The problem is definitely something to do with graphics because the program runs fine in its 'text' mode.

If anyone has had any similar issues with  any programs let me know if you have any ideas how to resolve this.

Thanks!

---

