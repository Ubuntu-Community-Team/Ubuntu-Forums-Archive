---
title: "Dockbarx leaves icon after closening."
date: 2011-06-15
forum: General Help
---

### Post by akzouu on 2011-06-15
So, Dockbarx leaves icon almost always, as I close any window, it disappear only if I move the cursor over it. Does anyone know how to fix this? Here's a link to demonstrate it, [http://www.youtube.com/watch?v=VdSKO4r0xkg](http://www.youtube.com/watch?v=VdSKO4r0xkg) .
I have ubuntu 11.04

Thanks, if u can help.

---

### Post by M7S on 2011-06-16
Sorry, which icon isn't removed when the window is closed? In the video I see you opening the eog and closing eog and the window dissapears directly after you've closed it.

---

### Post by akzouu on 2011-06-16
See, how dockbarx behave. I mean the window list. For example, as closening skype window, it is still in the dock.

---

### Post by M7S on 2011-06-16
Ok, now I see. I guess the problem is limited to programs that are in notification area? Can you post your log ~/.dockbarx/log/dockbarx.log?

---

### Post by akzouu on 2011-06-16
Here's the log:

INFO    | 2011-06-15 02:02:22,626    | DockbarX 0.44
INFO    | 2011-06-15 02:02:22,627    | DockbarX init
INFO    | 2011-06-15 02:02:27,779    | DockbarX reload
DEBUG    | 2011-06-15 02:02:28,593    | Xlib.protocol.request.QueryExtension
ERROR    | 2011-06-15 02:02:31,459    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,561    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,579    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,586    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,636    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,690    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:31,924    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:32,033    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:32,513    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:32,550    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:02:32,570    | TypeError: deopacify() takes exactly 2 arguments (1 given)
DEBUG    | 2011-06-15 02:03:26,513    | Xlib.protocol.request.QueryExtension
ERROR    | 2011-06-15 02:03:28,668    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:28,694    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:28,902    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:28,943    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:29,074    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:30,404    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:43,279    | Traceback (most recent call last):
ERROR    | 2011-06-15 02:03:43,280    |   File "/usr/lib/pymodules/python2.7/dockbarx/dockbar.py", line 450, in __on_window_closed
ERROR    | 2011-06-15 02:03:43,280    |     self.__remove_window(window)
ERROR    | 2011-06-15 02:03:43,281    |   File "/usr/lib/pymodules/python2.7/dockbarx/dockbar.py", line 616, in __remove_window
ERROR    | 2011-06-15 02:03:43,281    |     self.remove_groupbutton(group)
ERROR    | 2011-06-15 02:03:43,282    |   File "/usr/lib/pymodules/python2.7/dockbarx/dockbar.py", line 484, in remove_groupbutton
ERROR    | 2011-06-15 02:03:43,282    |     group.destroy()
ERROR    | 2011-06-15 02:03:43,282    |   File "/usr/lib/pymodules/python2.7/dockbarx/groupbutton.py", line 223, in destroy
ERROR    | 2011-06-15 02:03:43,283    |     self.button.destroy()
ERROR    | 2011-06-15 02:03:43,283    |   File "/usr/lib/pymodules/python2.7/dockbarx/groupbutton.py", line 1414, in destroy
ERROR    | 2011-06-15 02:03:43,284    |     self.deopacify()
ERROR    | 2011-06-15 02:03:43,284    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:43,916    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:45,020    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:46,845    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:48,841    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:49,333    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:49,630    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:51,525    | TypeError: deopacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:51,680    | TypeError: opacify() takes exactly 2 arguments (1 given)
ERROR    | 2011-06-15 02:03:52,763    | TypeError: deopacify() takes exactly 2 arguments (1 given)

---

### Post by M7S on 2011-06-16
Ok. Found the bug. I'll make a bug fix release next week. Until that a fix would be to turn of opacify (or to live with it). Thanks for reporting!

---

