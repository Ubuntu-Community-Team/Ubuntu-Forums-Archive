---
title: "Users are not shown in user admin GUI-tool"
date: 2009-10-22
forum: General Help
---

### Post by lundbymads on 2009-10-22
Problem: My users are not shown in the GUI-tool anymore

[IMG]http://dl.getdropbox.com/u/321655/Sk%C3%A6rmbillede-Brugerindstillinger.png[/IMG]

The users are still there in the /etc/passwd-file and they log in just fine.

The problem occured after a hard reboot. I had changed the home folder of one of the user accounts (I couldn't get the new folder path to stick after closing down the "Users and Groups"-application, the old settings kept coming back - despite the new folder had the right perm's). So I tried to do a brutal power down after changing the home folder but before closing "Users and Groups", hoping the new home folder path would stick. Silly me...).

What can solve this problem?

System: Ubuntu 9.10 32 bit

I've tried to reinstall gnome-system-tools.

---

### Post by dcstar on 2009-10-23
> **lundbymads said:**
> Problem: My users are not shown in the GUI-tool anymore
........
The users are still there in the /etc/passwd-file and they log in just fine.

The problem occured after a hard reboot. I had changed the home folder of one of the user accounts (I couldn't get the new folder path to stick after closing down the "Users and Groups"-application, the old settings kept coming back - despite the new folder had the right perm's). So I tried to do a brutal power down after changing the home folder but before closing "Users and Groups", hoping the new home folder path would stick. Silly me...).

What can solve this problem?

System: Ubuntu 9.10 32 bit

I've tried to reinstall gnome-system-tools.

Check the following files:

```
/etc/passwd
/etc/passwd-
/etc/shadow
/etc/shadow-
```

The "-" ones are the previous edit, you may have to replace the current ones with the old versions.

Otherwise this may help to recreate a new shadow file:

```
man pwconv
```

---

### Post by lundbymads on 2009-10-23
Hi David

Restoring the passwd and shadow files did not work... unfortunately. I also tried to run the command 
```
$sudo pwconv
```

but no luck.

Thanks for your reply.

---

