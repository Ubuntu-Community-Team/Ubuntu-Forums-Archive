---
title: "Ubuntu 10.04 won't show login screen, stuck at boot screen"
date: 2012-05-05
forum: General Help
---

### Post by link470 on 2012-05-05
Hello!  I have a fresh install of Ubuntu 10.04 64-bit installed on a laptop, and all I've done so far is install LibreOffice after removing OpenOffice, installed Flash Player, installed JRE 6u31, and installed all updates.  I also added Flash Player as a Firefox plugin to the two user profiles on the system.  Good so far.

The only other thing I've tried to do is hide one of the user accounts from the login screen, and to do this, I edited the /etc/gdm/gdm.schema file, and added the username I wanted to hide in the <default> tags of the file with the other system accounts.  After restarting, I get stuck at the Ubuntu login screen.  The dots never freeze up, and if I want, I can hit F5 and see Check battery state as the last item as [OK], and if I go alt+F5 and log in and startx, the gui desktop comes up.

Wondering if I somehow screwed up gdm with that edit to gdm.schema, I edited the file back to it's original state by removing the account I originally wanted hidden and restarting the laptop, but I still just got an endless boot screen.  I then reinstalled gdm completely, and that also didn't work.

I'd be happy to provide any information anyone needs for clarification.  I'm more just curious if I can fix this.  I know perfectly well that I could rebuild the laptop in an hour and have it back to where it should be, but I'm very curious as to what went wrong and how I can fix it.

Thanks!

---

### Post by link470 on 2012-05-08
Going to try rebuilding now and following the same steps as I did before, and restart after each one and see what went wrong.

---

### Post by miasmablk on 2012-05-08
perhaps something is hashed out in your gdm.schema that shouldn't be? maybe there is a .conf file somewhere you may need to edit like in "arch" gdm has to be added to rc.conf manually...sorry im not being much help im away from my main computer just throwing some ideas out there for ya :/

---

### Post by miasmablk on 2012-05-08
check your /etc/modules maybe as ubuntu doesn't have an rc.conf perhaps this may be some help

---

