---
title: "gnome-activity-journal won't start except as root"
date: 2012-08-23
forum: General Help
---

### Post by bturrie on 2012-08-23
I'm running ubuntu 12.04 64 bit on my system. gnome-activity-journal won't run under my user. When I try to run it from a terminal I get:


[INDENT]Traceback (most recent call last):
  File "/usr/bin/gnome-activity-journal", line 97, in <module>
    from src.main import PortalWindow
  File "/usr/share/gnome-activity-journal/src/main.py", line 31, in <module>
    from activity_widgets import MultiViewContainer, TimelineViewContainer, ThumbViewContainer
  File "/usr/share/gnome-activity-journal/src/activity_widgets.py", line 42, in <module>
    from supporting_widgets import DayLabel, ContextMenu, ContextMenuMolteplicity, StaticPreviewTooltip, VideoPreviewTooltip,\
  File "/usr/share/gnome-activity-journal/src/supporting_widgets.py", line 1757, in <module>
    AudioPreviewTooltip = AudioPreviewTooltip()
  File "/usr/share/gnome-activity-journal/src/supporting_widgets.py", line 726, in __init__
    fakesink = gst.element_factory_make("fakesink", "fakesink")
gst.ElementNotFoundError: fakesink
[/INDENT]

It will run if I use

[INDENT]sudo gnome-activity-journal[/INDENT]

It runs fine. Not sure why root should be required. Any suggestions?

---

