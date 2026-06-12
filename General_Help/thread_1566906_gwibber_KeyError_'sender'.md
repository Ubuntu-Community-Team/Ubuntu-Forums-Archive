---
title: "gwibber KeyError: 'sender'"
date: 2010-09-03
forum: General Help
---

### Post by whalogreg on 2010-09-03
When I try to run Gwibber from the menu nothing happens. When run in termial I get this error..

```


greg@greg-laptop:~$ gwibber

** (gwibber:4634): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4634): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4634): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 448, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 59, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 145, in setup_ui
    self.stream_view.set_state(self.model.settings["streams"] or DEFAULT_SETTINGS["streams"])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 439, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 427, in update
    self.message_view.render([self.navigation.selected_stream["view"]])
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 737, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 279, in render
    content = template.render(theme=util.get_theme_colors(), resources=resources, _=_, **kwargs)
  File "/usr/lib/pymodules/python2.6/mako/template.py", line 133, in render
    return runtime._render(self, self.callable_, args, data)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 364, in _render
    _render_context(template, callable_, context, *args, **_kwargs_for_callable(callable_, data))
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 381, in _render_context
    _exec_template(inherit, lclcontext, args=args, kwargs=kwargs)
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 414, in _exec_template
    callable_(context, *args, **kwargs)
  File "memory:0x1fdf290", line 207, in render_body
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 805, in render_messages
  File "memory:0x1fdf290", line 84, in message
  File "/usr/lib/pymodules/python2.6/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 317, in render_sidebar
KeyError: 'sender'

```

in system monitor "gwibber-service" is running, and occasionally my 'broadcast accounts' window pops up randomly. 

Gwibber worked for a few months on Lucid and just randomly stopped working.

Any ideas?

---

### Post by dr_saaron on 2010-11-06
I'm getting the exact same error.

---

