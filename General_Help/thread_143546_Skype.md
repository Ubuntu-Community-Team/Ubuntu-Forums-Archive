---
title: "Skype"
date: 2006-03-12
forum: General Help
---

### Post by Mr X on 2006-03-12
How do I change the **.rpm** file to the **.deb** file? What commands do I use?

---

### Post by kaamos on 2006-03-12
Alien.
```
sudo apt-get install alien
sudo alien -i name_of_skype_file.rpm
skype
```
You can find more info with "man alien" once alien is installed.

---

### Post by Mr X on 2006-03-12
I have the skype .rpm file on my desktop. Where would the location be?

Skype file name: skype-1.2.0.18-fc3.i586.rpm

---

### Post by kaamos on 2006-03-12
use "cd Desktop" to get to the desktop. You can use the command "ls" to list files and directories. Also note that all linux commands and file names are case sensitive. You can also make good use of tab to autocomplete the names (like typing "cd Des" and pressing tab).

---

