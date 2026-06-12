---
title: "Compiz/OpenGL corrupt after a recent Update."
date: 2010-10-12
forum: General Help
---

### Post by flxdms on 2010-10-12
Hello,

Err. So the title basically explains everything there is to explain. I turned my computer on and noticed there were over 100 updates to download. I downloaded them but for some odd reason, I kept getting errors. The update manager kept saying it could not update compiz-fusion and that some packages were already installed. The update manager told me to type sudo apt-get install -f to install compiz-fusion. I then restarted my computer after doing what the update manager asked me to do.

When I got to the desktop screen, the gnome bottom bar was frozen, my windows were unmovable and had lost their emerald skin. Anything related to windows management/compiz wasn't working anymore (and still isn't). I opened ccsm and noticed none of the options in the menu were selected. I tried to manually select them and got errors such as "Wobbly Windows requires OpenGL" and "OpenGL requires Composite". I also noticed some of the ccsm icons were looking odd. (They are showing as a "?" with a gear on a paper). When I click on more than 3 options, compiz closes. 

I also get this when it closes :

Info: No sexy-python package found, don't worry it's optional.
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Loading icons...
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 250, in ParseSettings
    plugin.Update ()
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'active_plugins'
Initializing gnomecompat options...done
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 1303, in ShowPlugin
    pluginPage = PluginPage(plugin)
  File "/usr/lib/python2.6/dist-packages/ccm/Pages.py", line 126, in __init__
    sortedGroups = sorted(plugin.Groups.items(), key=GroupIndexKeyFunc)
  File "compizconfig.pyx", line 939, in compizconfig.Plugin.Groups.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'main_menu_key'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Widgets.py", line 1420, in enable_plugin
    if conflict.Resolve ():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 380, in Resolve
    for setting in GetSettings(self.Plugin):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 396, in GetSettings
    display = group.Display.itervalues()
  File "compizconfig.pyx", line 945, in compizconfig.Plugin.Display.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'main_menu_key'
Initializing decor options...done
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Widgets.py", line 1420, in enable_plugin
    if conflict.Resolve ():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 380, in Resolve
    for setting in GetSettings(self.Plugin):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 396, in GetSettings
    display = group.Display.itervalues()
  File "compizconfig.pyx", line 945, in compizconfig.Plugin.Display.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'shadow_radius'
Initializing composite options...done
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ccm/Widgets.py", line 1420, in enable_plugin
    if conflict.Resolve ():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 341, in Resolve
    if con.Resolve():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 341, in Resolve
    if con.Resolve():
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 380, in Resolve
    for setting in GetSettings(self.Plugin):
  File "/usr/lib/python2.6/dist-packages/ccm/Utils.py", line 396, in GetSettings
    display = group.Display.itervalues()
  File "compizconfig.pyx", line 945, in compizconfig.Plugin.Display.__get__
  File "compizconfig.pyx", line 766, in compizconfig.Plugin.Update
KeyError: 'slow_animations_key'
Initializing fade options...done
Segmentation fault


Can anyone help me? I have tried uninstalling the compiz-related plugins by following a guide on the Ubuntu forums but when I tried removing some packages, it said they weren't existing. 

Thanks,

---

### Post by Ni85 on 2010-10-13
up and same problem for me...

---

### Post by flxdms on 2010-10-13
In case it helps, I am using Ubuntu 10.10 with Gnome.

---

### Post by cpmman on 2010-10-13
I had a compiz problem and followed this advice which corrected it:-
[B][I][U][URL="http://ubuntuforums.org/showpost.php?p=9964610&postcount=2"]
http://ubuntuforums.org/showpost.php?p=9964610&postcount=2[/URL][/U][/I][/B]

---

### Post by flxdms on 2010-10-13
> **cpmman said:**
> I had a compiz problem and followed this advice which corrected it:-
[B][I][U][URL="http://ubuntuforums.org/showpost.php?p=9964610&postcount=2"]
http://ubuntuforums.org/showpost.php?p=9964610&postcount=2[/URL][/U][/I][/B]

Thank you very much, this solved my problem.

---

### Post by emoguitarist06 on 2010-10-13
> **flxdms said:**
> Thank you very much, this solved my problem. =D!

Don't forget to use the Thread Tools link at the top to mark the thread solved :)

---

### Post by cpmman on 2010-10-13
> **flxdms said:**
> Thank you very much, this solved my problem.

I am pleased for you.  Would you goto your original post and mark "solved" via the thread tools.

edit: beaten to it!

---

### Post by Ni85 on 2010-10-13
> **cpmman said:**
> I had a compiz problem and followed this advice which corrected it:-
[B][I][U][URL="http://ubuntuforums.org/showpost.php?p=9964610&postcount=2"]
http://ubuntuforums.org/showpost.php?p=9964610&postcount=2[/URL][/U][/I][/B]

worked for me too
thanks

---

### Post by flxdms on 2010-10-23
> **emoguitarist06 said:**
> Don't forget to use the Thread Tools link at the top to mark the thread solved :)

Will do, lmao. I kinda went mia for a week.

---

### Post by canlang on 2010-10-26
wow, thax!!:)

---

