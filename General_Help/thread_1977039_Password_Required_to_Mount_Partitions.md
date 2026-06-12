---
title: "Password Required to Mount Partitions"
date: 2012-05-09
forum: General Help
---

### Post by Dennis N on 2012-05-09
Lubuntu 12.04: When mounting a hard drive partition from the pcmanfm file manager, the administrative user is now always asked for a password. This is not required in Ubuntu 12.04, or any previous Ubuntu (or Lubuntu) I have used. How would one restore the previous no password policy in Lubuntu? Thank you.

---

### Post by infectedorganism on 2012-05-09
> **Dennis N said:**
> Lubuntu 12.04: When mounting a hard drive partition from the pcmanfm file manager, the administrative user is now always asked for a password. This is not required in Ubuntu 12.04, or any previous Ubuntu (or Lubuntu) I have used. How would one restore the previous no password policy in Lubuntu? Thank you.

1. Open your terminal

2. Paste this into terminal and run:

   gksu leafpad /usr/share/polkit-1/actions/org.freedesktop.udisks.policy

*replace leafpad with your chosen text editor

3. Enter root password

4. Locate the id: (it should be near the top. line 26 for me):   <action id="org.freedesktop.udisks.filesystem-mount-system-internal">

5. When you found that id, look for line <allow_active>auth_admin_keep</allow_active>

6. Change 'auth_admin_keep' to 'yes' (example: <allow_active>yes</allow_active>)

* You can comment it out in case you want to change it back for some reason. <!-- <allow_active>auth_admin_keep</allow_active> -->

And then just put <allow_active>yes</allow_active> below the line you just commented out.

7. Save

---

### Post by Dennis N on 2012-05-09
Thanks - I really appreciate your help. I will make the change you give here when I get to my desktop computer.

Best regards - Dennis N

[I]Results:
Edited the policy file as suggested, and a password is no longer required. It is strange the Ubuntu has the same original action policy set, yet requires no password for administrator group, so something else is going on with Lubuntu or pcmanfm. Nevertheless, problem is solved. Thanks again.[/I]

---

