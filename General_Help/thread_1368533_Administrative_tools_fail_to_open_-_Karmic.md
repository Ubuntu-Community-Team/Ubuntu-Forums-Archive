---
title: "Administrative tools fail to open - Karmic"
date: 2009-12-30
forum: General Help
---

### Post by kiriyama9000 on 2009-12-30
Hello all, 
    I have been searching for help, but my criteria isn't turning up in any searches.

I'm running Ubuntu 9.10 and all of a sudden find myself unable to run certain administrative tools. 

Janitor, Update Manager, and Ubuntu Software Center refuse to launch at all.

I'm coming off the heels of a fresh install, though I'm sure that can't mean too much.

My account is the only on this machine besides root and I have administrative privileges.

How can I resolve this issue?
Thank you for your time!

---

### Post by wilee-nilee on 2009-12-30
What happens if you try and open synaptic?

---

### Post by kiriyama9000 on 2009-12-30
> **wilee-nilee said:**
> What happens if you try and open synaptic?
Synaptic does start and run, thankfully

---

### Post by sisco311 on 2009-12-30
Try to run them from a terminal (Applications -> Accessories -> Terminal)
and post the error message here.

```
update-manager
```
```
software-center
```

---

### Post by kiriyama9000 on 2009-12-30
> **sisco311 said:**
> Try to run them from a terminal (Applications -> Accessories -> Terminal)
and post the error message here.

```
update-manager
``````
software-center
```

kiriyama9000@UBUNTU9000:~$ update-manager
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 75, in <module>
    from DistUpgradeFetcher import DistUpgradeFetcherGtk
  File "/usr/lib/python2.6/dist-packages/UpdateManager/DistUpgradeFetcher.py", line 26, in <module>
    from ReleaseNotesViewer import ReleaseNotesViewer
  File "/usr/lib/python2.6/dist-packages/UpdateManager/ReleaseNotesViewer.py", line 33, in <module>
    class ReleaseNotesViewer(gtk.TextView):
AttributeError: 'module' object has no attribute 'TextView'


--------------------------------------------------------

kiriyama9000@UBUNTU9000:~$ software-center
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 40, in <module>
    import view.dialogs
  File "/usr/share/software-center/softwarecenter/view/dialogs.py", line 22, in <module>
    from pkgview import PkgNamesView
  File "/usr/share/software-center/softwarecenter/view/pkgview.py", line 28, in <module>
    class PkgNamesView(gtk.TreeView):
AttributeError: 'module' object has no attribute 'TreeView'



I tried both of these with sudo to no avail as well.

Thank you!!!

---

### Post by sisco311 on 2009-12-30
Try to reinstall libatk:
```
sudo apt-get update
sudo apt-get install --reinstall libatk1.0-0
```
[thread]540938[/thread]

---

### Post by kiriyama9000 on 2009-12-30
> **sisco311 said:**
> Try to reinstall libatk:
```
sudo apt-get update
sudo apt-get install --reinstall libatk1.0-0
```[thread]540938[/thread]
That didn't seem to do it.
Thanks though!

---

### Post by kiriyama9000 on 2009-12-30
Thanks!!!

It did work. I gave the machine a reboot and now everything runs normally!

---

