---
title: "Gnome-tweak tool not opening in 12.04"
date: 2012-06-16
forum: General Help
---

### Post by Teclas5 on 2012-06-16
Hey all, I'm having an issue with gnome-tweak in that it doesn't open at all. Normally I am able to find my own solutions, but this one is a bit hard for a novice like me to figure out. If it helps, I've added terminal output when I attempt to run it. Much appreciate the help!

 
 ```
ernesto@ernesto-GT5428:~$ gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 76, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 44, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 40, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 135, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 236, in <module>
    GSettingsSwitchTweak("org.gnome.settings-daemon.plugins.power", "lid-close-suspend-with-external-monitor"),
  File "/usr/lib/python2.7/dist-packages/gtweak/widgets.py", line 116, in __init__
    _GSettingsTweak.__init__(self, schema_name, key_name, **options)
  File "/usr/lib/python2.7/dist-packages/gtweak/widgets.py", line 105, in __init__
    options.get("summary",self.settings.schema_get_summary(key_name)),
  File "/usr/lib/python2.7/dist-packages/gtweak/gsettings.py", line 122, in schema_get_summary
    return self._schema._schema[key]["summary"]
KeyError: 'lid-close-suspend-with-external-monitor'
ernesto@ernesto-GT5428:~$ 

```

---

### Post by papisz on 2012-06-17
Hi,
I had the same problem. It happened to me today after installing gnome-tweak and gnome shell 3.4 from instructions on this site (in "14") [http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)
Previous version was working, so I've just removed this one
```
sudo apt-get remove gnome-tweak-tool
```
removed ppa:ricotz/testing repository from Synaptic in Settings->Repositories and installed version from official Ubuntu repository once again

```
sudo apt-get install gnome-tweak-tool
```

I know it's only a workaround, I'd gladly see a real solution.

---

### Post by ExSuSEusr on 2012-06-17
This most recent update really messed a lot of things up.  I have the same issue too - have tried the uninstall reinstall and nothing works.

I am not sure what they did - but seriously they really screwed a lot of things up.

---

### Post by flight@down on 2012-06-17
I did fix the issue commenting out line 236 of /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py.

```
sudo gedit /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py
```

Even if (from [https://lists.gnome.org/archives/commits-list/2012-June/msg01208.html](https://lists.gnome.org/archives/commits-list/2012-June/msg01208.html)) the option "lid-close-suspend-with-external-monitor" should be available in gnome 3.5.2, it is not listed using the command ```
gsettings list-recursively org.gnome.settings-daemon.plugins.power
``` so that means it is not really available causing the failure.

I know this is just a workaround (the option is missing for another issue) but for now is getting gnome-tweak-tool usable.

Hope that can help

---

### Post by Teclas5 on 2012-06-17
That helped fix the issue, many thanks papisz! ExSuSEusr, I agree, many things not working properly, yet aside from this issue, I was able to manage on my own. Glad to have the forums, that's for sure! :p Thanks again for the help!

---

### Post by CheeseManiac on 2012-06-18
[papisz]("http://ubuntuforums.org/member.php?u=1676829") thanks you so much!!! you resolved my problem!!

---

### Post by DeltaFee on 2012-06-21
I fixed it using this post:

[http://ubuntuforums.org/showthread.php?t=2005240&highlight=Gnome-tweak-tool](http://ubuntuforums.org/showthread.php?t=2005240&highlight=Gnome-tweak-tool)

---

