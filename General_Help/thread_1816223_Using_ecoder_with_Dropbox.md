---
title: "Using ecoder with Dropbox"
date: 2011-08-01
forum: General Help
---

### Post by winkyeah on 2011-08-01
Hi,
 
I am using the ecoder script ([http://sourceforge.net/projects/ecoder/](http://sourceforge.net/projects/ecoder/)) to try and edit some text files that reside in my /home/<my user>/Dropbox/Writings folder. When I tell ecoder to use that folder for it's root folder it complains that it cannot find it. 
 
Ecoder is installed to /var/www/code.
 
I created a group called www-pub that has my user and the www-data user. I then set the Writings folder to that group, keeping my user as the owner. Then I chmod 777 on the Writings folder and all subfolders (-R). Still doesn't work.
 
If I create a new folder under /tmp/drop and use the same permissions and group ecoder works fine. 
 
Can anyone give me any tips on what to try next?

---

