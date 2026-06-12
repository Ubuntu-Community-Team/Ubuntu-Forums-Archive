---
title: "Unable to update or install apps - FYI"
date: 2009-11-22
forum: General Help
---

### Post by theG33K on 2009-11-22
After a fresh install of 9.10 this morning I was able to update ok but after rebooting and trying to install apps from the Add / Remove app it times out. I first thought it was an issue with my install but looking into the issue it appears that us.archive.ubuntu.com is down. It cycled through all the IPs 91.189.88.30 - 45 before I stopped it, all IPs in range are timing out. 

I've tried on various others PCs (Windows included) and all report us.archive.ubuntu.com is down. Been down about a half hour now.

---

### Post by Uncle Spellbinder on 2009-11-22
No issues here. Tried on 2 different computers. Even [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) loads quickly.

---

### Post by Nonstop Crunchy on 2009-11-22
I have been having the same problem for about 3 hours here.  Tried to install Java on my son's PC so he could play a game and no luck, us.archive.ubuntu is down.  Tried running updates and get the same errors.

---

### Post by theG33K on 2009-11-22
[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) times out for me even on my windows PCs. Perhaps it's ISP DNS issues. 

The server at us.archive.ubuntu.com is taking too long to respond.

UPDATE: On a whim I just changed the DNS server settings on my router from my ISPs default which hijacks and redirects to there own 404 page and I was able to ping and hit the Ubuntu archive.

My ISP is COX (I'm in New England)and it looks like they are having DNS server issues. I changed from the default hijacking DNS servers to their alternative (non hijacking) and I am able to update now :)

---

