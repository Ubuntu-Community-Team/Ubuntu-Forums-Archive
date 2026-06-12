---
title: "Several issues after a 9.04 to 9.10 upgrade"
date: 2010-01-08
forum: General Help
---

### Post by dbruce100 on 2010-01-08
Did a standard upgrade outlined below:

[http://ubuntuforums.org/showthread.php?t=1375491](http://ubuntuforums.org/showthread.php?t=1375491)

Main issues are Firefox no longer works and gksudo nautilus stopped working. I also tried a different account that is rarely used, and firefox is toast there also.  Error info etc is in above link.  

Better then likely a permission or linking issue, but after removing and installing multiple time, I'm at a loss.  Any help would be greatly appreciated.

---

### Post by cariboo on 2010-01-08
Please don't create multiple threads on the same subject.

Have you created a new firefox profile? Press alt-F2 and type:

```
firefox -ProfileManager
```

For your sudo problem check your sudoers file, it should look like this:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by dbruce100 on 2010-01-08
> Please don't create multiple threads on the same subject.

Sorry, thought I'd posted in the wrong section.  

> firefox -ProfileManager

Created profile, same issue.  Profile was created under gksudo due to problem starting Firefox....which also means .mozilla is now root owned.....though I removed it and it is not recreated when Firefox is run without gksudo.  home dir has correct permissions.

Almost seems like is is stuck in the firefox.sh script.

> For your sudo problem check your sudoers file, it should look like this:

File is identical to yours.  gksudo will work with Gedit, just not Nautilus command.  Worked after upgrade and then just stopped.

---

### Post by dbruce100 on 2010-01-08
Update, after a reboot the gksudo nautilus works.  

Firefox still has issues.

---

### Post by dbruce100 on 2010-01-08
Update again:

Finally found a post with exactly my problem.  Still searching for the solution.....but have postponed the rollback:

[http://ubuntuforums.org/showthread.php?t=1305390](http://ubuntuforums.org/showthread.php?t=1305390)

---

