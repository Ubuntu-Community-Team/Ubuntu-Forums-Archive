---
title: "Help!!!"
date: 2011-10-16
forum: General Help
---

### Post by daniel.cotter on 2011-10-16
I used deja-dup to perform a backup in preparation for an upgrade to 11.10, and then I restored it to make sure it worked as it should.  It didn't.  On reboot, I get presented with the greeter, but when I log in, I get the error: "Cannot enter home directory.  Using /".  Next error is: "Could not update ICE authority file /.ICEAuthority"  Next comes "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)." Then "Could not apply the stored configuration for monitors ..." and some rapid errors all referring to permissions problems reaching my home directory.  It suggests I recreate the files or set the permissions so they can be accessed.

All the files are still there, and I can see them in a non-graphical interface as root, but I don't know how to fix it so it loads normally.  It seems like a display problem, because I cannot startx -- I get a server error.

I have tried to run duplicity to verify the backup, and it comes back saying everything is fine.

I backed up /home/me and /etc/X11, then restored them (there had been no changes in between) to /home/me, all in the GUI mode with deja-dup.


I don't know which logs to review to determine the source of the problem.  Any help would be greatly appreciated.

---

