---
title: "How do I apply user permissions to not just folders but also all files"
date: 2010-01-19
forum: General Help
---

### Post by ozguitarplayer on 2010-01-19
Hi,
I want to add my daughter as a user and give her full permissions to all the same folders and files that I use.
I have given her permission to folders and their sub folders however she doesn't have rwx on the individual files within the folders.
What is the command line to set this up?

Also with the command; 
```
chown -R root:root files
``` 
what is the -R for and when do I need or not need it?

Any help appreciated

---

### Post by nothingspecial on 2010-01-19
The -R means recursive, which will apply the permissions to all subfolders and files within them.

So the -R flag is what you need.

---

### Post by ozguitarplayer on 2010-01-19
Thanks,
I did use -R however when I switch users and go into say the mp3 folder she does not have rwx on the individual files.

---

### Post by nothingspecial on 2010-01-19
What you need to do is make a group. Put yourself and your daughter as members of that group, then

chown -R you:new_group mp3folder

chmod -R 775 mp3folder

---

### Post by ozguitarplayer on 2010-01-19
Thanks again, 
Have to go to work, I'll try later and post a reply.

---

