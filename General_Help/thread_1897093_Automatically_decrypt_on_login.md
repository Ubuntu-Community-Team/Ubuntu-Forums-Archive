---
title: "Automatically decrypt on login"
date: 2011-12-18
forum: General Help
---

### Post by roofusthedoofus1 on 2011-12-18
hello there.

After solving a different problem involving being unable to login, I am now having trouble with having my encrypted home folder being automatically decrypted once i log in.  At the moment i must log in, then manually decrypt.  All it involves is double clicking on Access-Your-Private-Data.desktop and entering a password but it would be good to have it done automatically.

So i deleted the auto-umount file in ~/.ecryptfs in a attempt to stop it dismounting when i logout so it'd still be mounted the next time i logged in or restart the laptop; and I left the file named auto-mount in the ~/.ecryptfs  - this did not work unfortunately.

I also tried removing the Encrypted Private directory setup altogether but this requires dismounting the encrypted private directory; when i do this everything gets encrypted again.

Anyone have any ideas?  Thanks in advance

---

