---
title: "bash script help"
date: 2010-10-02
forum: General Help
---

### Post by U_buntu on 2010-10-02
what command will cause a bash script to open and run another bash script?
I understand the opening other programs with a bash script, but not other scripts.

---

### Post by ridgeland on 2010-10-06
I do this in bash scripts, it's nothing special.
In the script
Monthly_Backup_ExtDrive.sh
I have a line
/Data/bin/scp_Laptop_Backup.sh
which runs the second script.

---

