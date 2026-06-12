---
title: "GLib error when trying to run Dwarf Therapist"
date: 2010-12-27
forum: General Help
---

### Post by ThisIsVictor on 2010-12-27
Hey all,

I'm trying to run Dwarf Therapist, a helper program for the game Dwarf Fortress. The program refused to run and I get the following error message: 

```
Could not open logfile for writing! "No such file or directory" 
ptrace attach: Operation not permitted

(<unknown>:3142): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(<unknown>:3142): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed
victor@victor-laptop:~$ DwarfTherapist 
Could not open logfile for writing! "No such file or directory" 
ptrace attach: Operation not permitted

(<unknown>:3178): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GObject'

(<unknown>:3178): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

```

I'm running Ubuntu 10.10. Any help would be great, thanks!
--Victor

---

