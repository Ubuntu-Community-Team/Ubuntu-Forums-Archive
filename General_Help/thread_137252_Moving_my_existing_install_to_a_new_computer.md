---
title: "Moving my existing install to a new computer"
date: 2006-02-27
forum: General Help
---

### Post by unperson on 2006-02-27
I have an existing install of Breezy on my desktop at home.  I just got a new machine, which I'd like to start using instead.  Obviously, I *could* do this by moving my hard drive to the new machine and installing a new copy of Breezy on the root partition (/home is a separate patition), but then I'd have to install, uninstall, and configure software on the new Breezy install to get it back the way I'd like it.

On the other hand, I could just move the HD to the new machine just use the install from the old machine that is on the root partition now.  But since the new machine has different hardware (basically all different except for the HD) presumably all the hardware related configuration would be wrong.

Is there some way for me to put the HD in the new computer and get it to re-do all hardware detection and configuration the way Ubuntu would during an install?

---

### Post by stalefries on 2006-02-27
I don't think so. If it was possible, it seems like it would be harder than just doing a new install, and jotting down all the changes you made on your original system.

---

### Post by darth_vector on 2006-02-27
if you back up the contents of /etc and you restore the files as necessary you should keep most of your config, though you will still have to re-install the OS and all of the software.

needless to say, you probably want to back up /home as well.

---

