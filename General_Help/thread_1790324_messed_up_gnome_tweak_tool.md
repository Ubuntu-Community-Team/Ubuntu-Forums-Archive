---
title: "messed up gnome tweak tool"
date: 2011-06-24
forum: General Help
---

### Post by u-noob-tu on 2011-06-24
the other day gnome tweak tool 3.0.5 was released with support for installing extensions in the app itself. i downloaded the source thinking that installing it would just overwrite the previous version. well, i guess it didnt, cuz now i cant get the old version to start or the new one. nothing happens. i tried uninstalling the previous version, but the new one still wont start. its kinda bugging me cuz i logged out and my theme was gone, and i cant go back to change it. how can i sort this out?

---

### Post by u-noob-tu on 2011-06-25
heres some more info. i tried running gnome-tweak-tool in the terminal and i get this error message: ```
ryan@ryan-Studio-1737:~$ gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/local/bin/gnome-tweak-tool", line 93, in <module>
    MainWindow()
  File "/usr/local/bin/gnome-tweak-tool", line 49, in __init__
    model)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/tweakview.py", line 40, in __init__
    self._model.load_tweaks()
  File "/usr/local/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 103, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/tweaks/tweak_nautilus.py", line 49, in <module>
    DesktopIconTweak(),
  File "/usr/local/lib/python2.7/dist-packages/gtweak/tweaks/tweak_nautilus.py", line 30, in __init__
    **options)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/widgets.py", line 107, in __init__
    _GSettingsTweak.__init__(self, schema_name, key_name, **options)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/widgets.py", line 99, in __init__
    self.settings = GSettingsSetting(schema_name, **options)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/gsettings.py", line 66, in __init__
    _SCHEMA_CACHE[schema_name] = _GSettingsSchema(schema_name, **options)
  File "/usr/local/lib/python2.7/dist-packages/gtweak/gsettings.py", line 34, in __init__
    assert(os.path.exists(schema_path))
AssertionError
```

---

### Post by u-noob-tu on 2011-06-25
okay, i really messed something up, cuz i just reinstalled gnome shell and the problem is still there. i think its a python error.

---

### Post by bmbaker on 2011-06-26
hmmph! i thought i would check if it works on my machine,......... nope it doesn't run at all!!

---

### Post by bmbaker on 2011-06-26
ya i am getting the same terminal output !!

```
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 84, in <module>
    MainWindow()
  File "/usr/bin/gnome-tweak-tool", line 47, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 38, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 107, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 25, in <module>
    from gi.repository import GLib
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 249, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py", line 39, in <module>
    class _VariantCreator(object):
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py", line 42, in _VariantCreator
    'b': GLib.Variant.new_boolean,
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 163, in __getattr__
    raise TypeError("unable to create a wrapper for %s.%s" % (info.get_namespace(), info.get_name()))
TypeError: unable to create a wrapper for GLib.Variant

```

---

### Post by u-noob-tu on 2011-06-27
I couldn't get it fixed, so I just reinstalled ubuntu and gnome 3.

---

### Post by bmbaker on 2011-06-28
i looked into it a bit and then tried ppa-purge on ricotz/staging and gnome-tweak works again!
when i re-activated ricotz/staging ppa it broke gnome-tweak again!
i think that soemething isn't talking nice to each other! i will wait and see!

---

