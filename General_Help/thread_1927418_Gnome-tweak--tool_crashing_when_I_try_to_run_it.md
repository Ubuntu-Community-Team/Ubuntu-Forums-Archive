---
title: "Gnome-tweak--tool crashing when I try to run it"
date: 2012-02-18
forum: General Help
---

### Post by canhoto on 2012-02-18
Hi.

I've installed gnome-tweak-tool, but I can't run it. Whenever I try to run it, it crashes before I can see anything.

Trying from the terminal, I have the following output:

> CRITICAL: Error parsing schema org.gnome.shell (/usr/share/glib-2.0/schemas/org.gnome.shell.gschema.xml)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/gsettings.py", line 45, in __init__
    summary = key.getElementsByTagName("summary")[0].childNodes[0].data
IndexError: list index out of range
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 145, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 38, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 123, in __init__
    v = map(int,proxy.version.split("."))
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 46, in version
    return json.loads(self.execute_js('const Config = imports.misc.config; Config.PACKAGE_VERSION'))
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
TypeError: expected string or buffer
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 76, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 44, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 40, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 131, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_font.py", line 24, in <module>
    GSettingsRangeTweak("org.gnome.desktop.interface", "text-scaling-factor", adjustment_step=0.1, group_name=TWEAK_GROUP_FONTS),
  File "/usr/lib/python2.7/dist-packages/gtweak/widgets.py", line 129, in __init__
    _min, _max = self.settings.get_range(key_name)[1]
ValueError: too many values to unpack
Any help, please?

---

