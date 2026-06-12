---
title: "Can't access home directory in GUI"
date: 2011-10-16
forum: General Help
---

### Post by daniel.cotter on 2011-10-16
I just posted this with the title HELP!!!, but maybe y'all are boycotting the nondescript title, so here it is with a more relevant title:

I used deja-dup to perform a backup in preparation for an upgrade to 11.10, and then I restored it to make sure it worked as it should. It didn't. On reboot, I get presented with the greeter, but when I log in, I get the error: "Cannot enter home directory. Using /". Next error is: "Could not update ICE authority file /.ICEAuthority" Next comes "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)." Then "Could not apply the stored configuration for monitors ..." and some rapid errors all referring to permissions problems reaching my home directory. It suggests I recreate the files or set the permissions so they can be accessed.

All the files are still there, and I can see them in a non-graphical interface as root, but I don't know how to fix it so it loads normally. It seems like a display problem, because I cannot startx -- I get a server error.

I have tried to run duplicity to verify the backup, and it comes back saying everything is fine.

I backed up /home/me and /etc/X11, then restored them (there had been no changes in between) to /home/me, all in the GUI mode with deja-dup.


I don't know which logs to review to determine the source of the problem. Any help would be greatly appreciated.

---

### Post by daniel.cotter on 2011-10-18
OK,  i have had a lot of lookers, but no responses.  Hoping if i update the thread with the latest, someone may be prompted to speak up.

I discovered that root owned everything, instead of me.  I think that's because I su'd in order to create /backup, which is where I wanted to store the backup of /home/me.

I may have backed up and restored as root as well.  Anyway, I chowned /home/me back to me, recursively, and everything comes up when I log in, but I am getting strange behaviors, too many to remember, and very intermittent.  One thing that is predictable is that the login keyring prompt that comes up will no longer accept my pw, as it always did.  Now I need the root password (Which I have set and know).  I also have an intermittent problem opening some "Places" from the graphical menu.  Sometimes they open, and sometimes I get the attached error message.

It looks lie somehow root owns /home/me, and chowning the directory somehow allows me to use it, mostly.

First, how do I let Ubuntu fix it for me, and, secondly, will upgrading from 11.04 to 11.10 just make the problem go away?

Thanks for any advice you can offer

---

