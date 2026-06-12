---
title: "Can't shutdown as normal user in 10.04"
date: 2011-04-26
forum: General Help
---

### Post by cleiton-xavier on 2011-04-26
I would like to shutdown the system as normal user, so i went through > System Settings - Advanced -> Login Manager - shutdown  and selected "everybody" for the ' Allow shutdown option'. I also went to > System Settings -> Session Manager - General and marked "Offer shutdown options" and in > Session Manager -  Default Leave Option I checked  "Turn off computer".  Again I gave a look In the /etc/kde4/kdm/kdmrc file and saw that in the > [X-*-Core] and [X-:*-Core]  parts of the file, the lines "AllowShutdown=All" were present. Finally I changed the ownership of reboot and shutdown from the root to my user, but he keeps wondering about the root password.

Any ideas?

BTW, what is the difference between  > [X-*-Core]  and >  [X-:*-Core] . The second one is the one that it is modified when I selected "everybody" for the "Allow shutdown option'. So the first one would be a kind of a backup's configuration?

---

