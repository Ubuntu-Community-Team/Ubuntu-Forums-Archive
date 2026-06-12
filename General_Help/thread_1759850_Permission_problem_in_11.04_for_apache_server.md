---
title: "Permission problem in 11.04 for apache server"
date: 2011-05-16
forum: General Help
---

### Post by gwu777 on 2011-05-16
Hi guys,

I know this subject has been covered so many times in the forum, but it all sound rather confusing and everybody seems to have a different story and solution, I am quite scared to play around permissions and stuff and mess up everything.

My apache2 local server was working perfectly before upgrading to natty, I had configured a site via [FONT=monospace]a[/FONT]2dissite && a2ensite, when going to [http://localhost](http://localhost) everything worked fine. Now, after the upgrade, I got

> 403 forbidden - You don't have permission to access / on this server

I have purged and reinstalled apache and all dependencies, same problem. When I change the site to the default one /var/www it works, if I create a www symlink in the /var/, I get the same permission error. It is then a permission problem, but which and why? I am not aware having changed permission on my /home/user/webdevelopment/www/ folder.

So far the solution seem to be to chmod /home/ to 755 as it seems that apache needs the whole path to be executable. I am not at ease with this solution as it used to work before without it. If it is what I need to do, how do I do that exactly?

from what I understood, apache needs

---

### Post by gwu777 on 2011-05-16
OK, i found the problem.

I am using quite a lot of symlink to go around my home directory and dropbox, despite changing a lot of permission on my home folder, it never worked. That is until I found that my original dropbox folder was not assigned any group, added my group and everything works fine.

VERY stupid problem, and I would love to know why my dropbox folder, created by dropbox didn't have the necessary permission any more? However this is for an other thread and time!

Cheers.

---

