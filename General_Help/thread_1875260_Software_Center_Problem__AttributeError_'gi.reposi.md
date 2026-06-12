---
title: "Software Center Problem : AttributeError: 'gi.repository.Gtk'"
date: 2011-11-04
forum: General Help
---

### Post by lif2k3 on 2011-11-04
I just ran "apt-get upgrade && apt-get dist-upgrade" then upgrade process and everything went normal, until I found this error when opened my Software Center :

```

root@lif2k3buntu:/home/lif2k3# software-center
software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 33, in <module>
    from gi.repository import Gtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 523, in <module>th
    class FontSelectionDialog(Gtk.FontSelectionDialog, Dialog):
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 105, in __getattr__
    self.__name__, name))
AttributeError: 'gi.repository.Gtk' object has no attribute 'FontSelectionDialog'

```

Any help?
sorry for my bad english, thank you :)

---

### Post by lkjoel on 2011-11-04
I have the exact same problem. I'm using Precise Pangolin 12.04, and I didn't have the problem in Oneiric 11.10.

---

### Post by lif2k3 on 2011-11-05
Need help.. Bump..

---

### Post by boucoeur on 2011-11-05
Va dans Synaptic, fait "Fichier, enregistrer les sélections sous"
en cochant la case "Enregistrer l'état complet".
Une fois que c'est fait tu fais "Lire les sélections" en choisissant le fichier que tu as enregistré et tu appliques les changements.
Une mise à jour se fais et miracle ça marche à nouveau....
Du moins chez moi qui avait la même erreur.

---

### Post by lif2k3 on 2011-11-05
> **boucoeur said:**
> Va dans Synaptic, fait "Fichier, enregistrer les sélections sous"
en cochant la case "Enregistrer l'état complet".
Une fois que c'est fait tu fais "Lire les sélections" en choisissant le fichier que tu as enregistré et tu appliques les changements.
Une mise à jour se fais et miracle ça marche à nouveau....
Du moins chez moi qui avait la même erreur.

duuuhh, I didn't know exactly what you mean, even I have translated that by Google Translate :(

---

### Post by raja.genupula on 2011-11-05
> **boucoeur said:**
> Va dans Synaptic, fait "Fichier, enregistrer les sélections sous"
en cochant la case "Enregistrer l'état complet".
Une fois que c'est fait tu fais "Lire les sélections" en choisissant le fichier que tu as enregistré et tu appliques les changements.
Une mise à jour se fais et miracle ça marche à nouveau....
Du moins chez moi qui avait la même erreur.

Hi man , small suggestion please type in english.
Thank you.

---

### Post by lif2k3 on 2011-11-05
Glad.. it's solved.. when I retrieved new updates, so I upgraded them..  :)

```

root@lif2k3buntu:/home/lif2k3# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gtk-3.0 gnome-shell handbrake-cli
  handbrake-gtk libgail-3-0 libgail-3-common libgirepository-1.0-1 libgtk-3-0
  libgtk-3-bin libgtk-3-common upstart virtualbox-4.1
14 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 91.6 MB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? y


```

thank you :)

---

