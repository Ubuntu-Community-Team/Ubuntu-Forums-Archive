---
title: "Post subject: pyvoice error: you do not have PyGtk-2 properly installe"
date: 2006-02-06
forum: General Help
---

### Post by shams2 on 2006-02-06
hi,
i installed the gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 with all neccessay files and other plugins in ubuntu, when for test i run the pyvoice in terminal this is the error:
/usr/lib/python2.4/ihooks.py:172: RuntimeWarning: Python C API version mismatch for module gobject: This Python has API version 1012, module gobject has version 1011.
return imp.load_dynamic(name, filename, file)
You do not have PyGtk-2 properly installed.
that is right the pyGtk is not installed properly because it is upacked to the /opt/gnome2/ and i don't know where to put these files?

---

### Post by dcstar on 2006-02-06
[QUOTE=shams2]hi,
i installed the gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 with all neccessay files and other plugins in ubuntu, when for test i run the pyvoice in terminal this is the error:
/usr/lib/python2.4/ihooks.py:172: RuntimeWarning: Python C API version mismatch for module gobject: This Python has API version 1012, module gobject has version 1011.
return imp.load_dynamic(name, filename, file)
You do not have PyGtk-2 properly installed.
that is right the pyGtk is not installed properly because it is upacked to the /opt/gnome2/ and i don't know where to put these files?[/QUOTE]
Assuming this is the Python2.4-gtk2 package, why not just install that from Synaptic?

---

