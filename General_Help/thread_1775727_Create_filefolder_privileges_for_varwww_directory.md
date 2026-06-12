---
title: "Create file/folder privileges for /var/www directory"
date: 2011-06-05
forum: General Help
---

### Post by Beta_Grumm on 2011-06-05
I just set up LAMP and installed a php editor on my 11.04 box. I fired up the editor and went to create a new folder in the www directory to start creating new files.

Lo and behold I can't.
My question is two fold:
1: Is there another place that I should be using to hold my web files other than /var/www?

2: How can I initiate sufficient privileges so that I can simply right click -> create folder/file with out having to open a term and sudo mkdir every time?

Thanks.

---

### Post by Dave_L on 2011-06-05
Create a subdirectory of /var/www and change its owner to USER:


```
sudo mkdir /var/www/subdir1
sudo chown USER:USER /var/www/subdir1
```

---

### Post by Beta_Grumm on 2011-06-05
I get the following:

chown: invalid user: 'USER:USER'

---

### Post by Dave_L on 2011-06-05
"USER" was an example.  Replace it with your user name.

Be careful to only apply chown to a subdirectory of /var/www.

Changing the entire /var/www directory might mess up the web server; I'm not sure about that. And changing the whole /var directory would definitely mess up your system.

---

### Post by Beta_Grumm on 2011-06-05
Solved.

Much appreciated.

---

