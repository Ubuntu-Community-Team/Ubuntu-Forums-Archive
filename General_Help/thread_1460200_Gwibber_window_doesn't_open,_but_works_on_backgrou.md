---
title: "Gwibber window doesn't open, but works on background"
date: 2010-04-22
forum: General Help
---

### Post by daas88 on 2010-04-22
I'm having a issue with gwibber: the window doesn't open, but I can tell it's working because I can tweet via Me menu. Also, the "microblogging" arrow/checkbox is active in the messaging-menu.

The window opens without problems in my dad's session, so I guess that if I delete some config file in my /home it will get fixed. Any idea of where are the gwibber config files? I couldn't find them =/

This is my terminal output when executing gwibber:
```
daniel@solid:~$ gwibber

** (gwibber:3967): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3967): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3967): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 447, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 58, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 119, in setup_ui
    self.message_target = gwui.AccountTargetBar(self.model)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 647, in __init__
    self.render()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 685, in render
    accounts=self.accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 267, in render
    self.web_settings.set_property("default-font-size", int(font_size))
ValueError: invalid literal for int() with base 10: '8.2998046875'
daniel@solid:~$ 

```

Edit: I've deleted almost all the hidden files on my home folder, and it worked the first time I used gwibber, but after the next boot the problem came back...

---

### Post by notquitemichael on 2010-04-30
you need to either change your font size to a whole number, or if you're feeling a bit braver: monkey-patch your gwibber file.

to do this edit /usr/lib/python2.6/dist-packages/gwibber/gwui.py with superuser rights, i.e.:
gksudo gedit /usr/lib/python2.6/dist-packages/gwibber/gwui.py

go to link 267 and change the **int**(font_size) to **eval**(font_size)

the error is happening because your whoever wrote the script didn't expect people to have font sizes which were not whole numbers. :)

---

### Post by daas88 on 2010-04-30
I think I'll feel brave and edit the file :P
As you might have noticed, I'm a perfectionist :oops:
Thanks a lot!

---

### Post by seriyPS on 2011-02-06
> **notquitemichael said:**
> you need to either change your font size to a whole number, or if you're feeling a bit braver: monkey-patch your gwibber file.

to do this edit /usr/lib/python2.6/dist-packages/gwibber/gwui.py with superuser rights, i.e.:
gksudo gedit /usr/lib/python2.6/dist-packages/gwibber/gwui.py

go to link 267 and change the **int**(font_size) to **eval**(font_size)

the error is happening because your whoever wrote the script didn't expect people to have font sizes which were not whole numbers. :)
eval==evil ))
replace it to float(font_size)

---

### Post by rbonazzo on 2011-04-06
Hi after an Ubuntu update I have receive this notification error:
** (gwibber:4641): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:4641): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:4641): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 87, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 620, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 71, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 251, in setup_ui
    self.stream_view.set_state(streams)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 410, in set_state
    self.update()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 397, in update
    self.messages.update(self.navigation.selected_stream)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 751, in update
    self.messages = self.message_view.render([selected_stream], count)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 813, in render
    accounts=accounts)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 256, in render
    content = template.render(theme=util.get_theme_colors(), util=util, resources=resources, _=_, **kwargs)
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/template.py", line 133, in render
    return runtime._render(self, self.callable_, args, data)
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 364, in _render
    _render_context(template, callable_, context, *args, **_kwargs_for_callable(callable_, data))
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 381, in _render_context
    _exec_template(inherit, lclcontext, args=args, kwargs=kwargs)
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 414, in _exec_template
    callable_(context, *args, **kwargs)
  File "memory:0x9bc652c", line 78, in render_body
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 862, in render_messages
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 466, in render_message
  File "base_mako", line 427, in messagebox
  File "base_mako", line 554, in render_messagebox
  File "base_mako", line 443, in body
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 489, in render_sidebar
  File "/usr/local/lib/python2.6/dist-packages/Mako-0.2.5-py2.6.egg/mako/runtime.py", line 255, in <lambda>
    return lambda *args, **kwargs:callable_(self.context, *args, **kwargs)
  File "base_mako", line 242, in render_image
  File "base_mako", line 188, in profile_url
  File "base_mako", line 795, in render_profile_url
KeyError: u'identica'

Pls any help

regards
Rinaldo

---

