---
title: "default 644 permissions"
date: 2010-08-12
forum: General Help
---

### Post by Nimridil on 2010-08-12
Hello dear Ubuntu community
Back in the days when I used windows I wrote a little website in jsp. It has forms that take text files from users, then java reads names of elements from those, puts together a subset with only those from a database that contains nuclear reactions data, zips the subset, and shows user a link to the archive. It all worked fine there. I use apache tomcat to run it, btw. Now, in Ubuntu, when it creates the .zip files they are somehow given 644 permissions, so my program can't write into them and they stay 0 bytes in size.
The tomcat webapps folder is located at /var/lib/tomcat6/webapps/
Since I figured I would always have to sudo to change something there I put my site in /home/myaccount/site/ and put a symbolic link to that place in the webapps folder.
The zip files are created in /home/myaccount/temp/
So it's really weird that I should get some other permissions there for new files besides 755. Besides that, when I to use umask in the temp folder it does change the permissions that new files get if I create them by hand, i.e. with touch, but those zips are still created with 644!
Does anybody have any idea how to solve this :confused:
I'm most likely going to host the site on a linux running server, so, I guess I might get the same issue there, too.

---

