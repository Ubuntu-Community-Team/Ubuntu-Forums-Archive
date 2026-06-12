---
title: "Permissions on shared folder (Apache + FTP)"
date: 2010-09-30
forum: General Help
---

### Post by martinlall on 2010-09-30
Hi,

I've got folder /srv/www/site1 that's owned by www-data:www-data (Apache).

Now I need to give FTPuser1:ftpusers r/w access to the same folder, but all my attempts are gone bad. How should I exactly do it?

---

### Post by martinlall on 2010-09-30
Hi,

I'm answering to my question myself. If anyone has better or more secure way, let me know.
The key is/was to set /srv/www folder permissions to 775 not 755.

[I]Shortly to newbies: **7** gives read-write to owner, **5** gives read to group and **5** for public (**755**), 
**775** gives r/w(**7**) for owner, r/w(**7**) for group and read(**5**) for public.[/I]

As I said, the folder (srv/www) permissions (you can get them by ls -l) was 755 and ls -l showed the owner to be www-data (aka apache default user) and group www-data.
All I did was adding secondary group for FTPuser1 to be www-data. And Voila.

Good luck!

---

