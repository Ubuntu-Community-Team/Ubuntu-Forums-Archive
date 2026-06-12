---
title: "Gtk+ / lvm"
date: 2010-07-18
forum: General Help
---

### Post by Johnius on 2010-07-18
I am trying to extend my LVM and didn't feel like dealing with the terminal commands, so I downloaded system-config-lvm.  But when I run it, I get the following readout:

```
sudo system-config-lvm 
Traceback (most recent call last):
  File "/usr/share/system-config-lvm/system-config-lvm.py", line 50, in <module>
    from Volume_Tab_View import Volume_Tab_View
  File "/usr/share/system-config-lvm/Volume_Tab_View.py", line 11, in <module>
    from Properties_Renderer import Properties_Renderer
  File "/usr/share/system-config-lvm/Properties_Renderer.py", line 33, in <module>
    import gnome
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gnome/_gnome.so: invalid ELF header 
```

Is there something I can do to make this work correctly?  Thanks in advance!

---

### Post by Exp HP on 2010-07-18
ELF errors usually indicate that you are using the wrong version of the file for your processor or architecture (for instance, running a 32-bit program on a 64-bit system).  Where did you get the file?  Can you look for other versions of the file?

---

### Post by Johnius on 2010-07-18
Thanks for your fast response.  I didn't get the file anywhere.  I just installed a clean copy of Kubuntu 10.04 LTS a couple of weeks ago.  I installed the LVM manager and it worked for a couple of days.  The only thing I can figure is that I updated a couple of packages (recommended by KPackageKit) and that would have caused the problem.  Is there a way to re-parse the _gnome.so file?

---

