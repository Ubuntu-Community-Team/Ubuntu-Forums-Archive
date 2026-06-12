---
title: "Time Change - Doesn't Work"
date: 2010-02-23
forum: General Help
---

### Post by Captain_MDS on 2010-02-23
Installed 9.10, time is 6 hours off. I selected "USA Central" and tried to change manually without any success. Any ideas?
Thanks, 
Captain_MDS

---

### Post by gmargo on 2010-02-23
It thinks your hardware clock is set to UTC and it's not.  Or vice versa :)

Check the file **/etc/default/rcS** and there should be an entry like **UTC=no** (or yes).  Toggle it.

---

### Post by Captain_MDS on 2010-02-23
Thanks, I'm a "newby" and computer dumb. How do I do this? Where do I type that command?

---

### Post by gmargo on 2010-02-23
To start the gedit editor with root privileges, type ALT-F2 to bring up a "run" prompt.  Enter
```

gksu gedit /etc/default/rcS

```Enter your password when it prompts you. Then change the UTC value, save the file, quit the editor, and reboot.

---

### Post by Captain_MDS on 2010-02-23
Thanks....

---

