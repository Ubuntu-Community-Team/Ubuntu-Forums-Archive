---
title: "Help with startup script"
date: 2011-03-24
forum: General Help
---

### Post by Wug on 2011-03-24
I am trying to make a startup script that executes a simple php script at boot.  The stipulation is that it must be run after fstab is processed because it requires access to a volume that fstab mounts.  As it is, it doesn't seem to be running properly at startup, and I suspect that it is simply running before the volume is mounted.  The script does not need root access.  If I run it once I login, it works fine.

Also, is there a way to determine the output of a startup script?

I am have configured a bash script called module.sh that cd's to the scripts directory (in the external volume) and then executes the script.  I didn't forget the ampersand after the php invocation.  I used update-rc.d module.sh defaults to configure it.

---

### Post by Wug on 2011-03-24
edit - it does seem that it's actually running, it just doesn't show up in the process manager or anything... odd

i guess this can be marked as solved, but it would still be nice if some of the questions in the OP were answered.

---

