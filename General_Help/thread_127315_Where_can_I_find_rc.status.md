---
title: "Where can I find rc.status"
date: 2006-02-08
forum: General Help
---

### Post by StoneyNebula on 2006-02-08
I have a script that needs rc.status.  I have looked in /etc/rc.* and done a find but can't seem to locate it.  A Google for it gets me loads of scripts that reference it, but I can't find the script itself - would appreciate it if someone could point me in the correct direction.

Thanks,

Stoney

---

### Post by lamego on 2006-02-08
I believe there is no rc.status on Debian based distros.
The equivalent should be "update-rc.d" .

---

### Post by dcstar on 2006-02-08
[QUOTE=StoneyNebula]I have a script that needs rc.status.  I have looked in /etc/rc.* and done a find but can't seem to locate it.  A Google for it gets me loads of scripts that reference it, but I can't find the script itself - would appreciate it if someone could point me in the correct direction.

Thanks,

Stoney[/QUOTE]
As far as I can see, this is not in Ubuntu/Debian Linux, it is used in some other distributions.

---

### Post by StoneyNebula on 2006-02-08
[QUOTE=lamego]I believe there is no rc.status on Debian based distros.
The equivalent should be "update-rc.d" .[/QUOTE]

Great - thanks for the tip, script works a treat now :) 

Stoney

---

