---
title: "Problem with a AdobeAir App. Thoughts?"
date: 2009-09-29
forum: General Help
---

### Post by MasterNetra on 2009-09-29
I'm trying to run a app called Finetune, and it wouldn't run from shortcut so I copied and paste its command into terminal and it had this to say:
```
ME:~$ '/opt/Finetune'/'FinetuneDesktop'/bin/'FinetuneDesktop'
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
```

The module is installed and for the fun of it I attempted to use getlib on the command (probably did it wrong too):
```
ME:~$ getlibs '/opt/Finetune'/'FinetuneDesktop'/bin/'FinetuneDesktop'
This application isn't missing any dependencies
```

Any thoughts?

---

### Post by MasterNetra on 2009-09-29
Bump - Unresolved

---

### Post by cariboo on 2009-09-29
The question may be better answered in General Help. Moved.

---

### Post by MasterNetra on 2009-09-29
Thus far nothing still -.-

---

### Post by MasterNetra on 2009-09-30
Bump - Unresolved

---

### Post by P4man on 2009-09-30
Googling your error gives me this:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

---

### Post by MasterNetra on 2009-09-30
> **P4man said:**
> Googling your error gives me this:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

nice...I knew there was a reason I stuck with 32bit Ubuntu...and now I'm reminded why. x.x

---

