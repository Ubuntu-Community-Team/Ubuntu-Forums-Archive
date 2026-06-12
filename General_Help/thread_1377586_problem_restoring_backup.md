---
title: "problem restoring backup"
date: 2010-01-10
forum: General Help
---

### Post by mickeyf on 2010-01-10
short story: tried to upgrade from 8.10 to 9.04. Way too many problems. Reinstalled 8.10. Now I'm trying to copy my carefully backed up /home folder to the new installation.

I did not user tar, just directly copied the files to an external drive. Now when I try to copy them back, using several variations along the lines of:

sudo cp -Rf backup-folder /home

I get a screen full of 

"Cannot stat 'some-filename' file or directory does not exist.

I have started out in the backup directory, and can browse to it. The files and folders do exist. How could the error message list the name if the file was not there. Surely it's not referring to the empty folder? That the whole point of copying it there.

Thinking it could be a permissions problem, I also tried 'sudo chown -Rv * myname:mygroup' but it complained for every file that I did not have permission. How can I not have permission after sudo? What's the point of that? 

Could someone please educate me?

Thanks,

---

