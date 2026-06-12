---
title: "change permissions on file owned by root"
date: 2009-08-30
forum: General Help
---

### Post by DrScum on 2009-08-30
After the latest recommended update I cannot connect anymore to several shares on my linux machine from other machines being part of the home network.
The reason is that the drives are no longer shared. If I want to share them again I get the message that the permissions can't be changed since they are owned by root. 
How can I logon as root and change permissions? I know the su command but I don't know the terminal command to change permissions.
It's sad that these things happen with updating. It makes you hesitate to update your system.

---

### Post by Liolikas on 2009-08-30
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by dtrot55 on 2009-08-30
i have been having the same issue with my 2nd hard drive...a somewhat fix is to do this:

gksudo nautilus

then go select your file and do preferences and then change the user to your username and give yourself full read and write capabilities.

hope this helps

---

### Post by credobyte on 2009-08-30
You can change the owner by executing the following command:
```
sudo chown -R user:user /disk/path
```
[COLOR=Gray]** Replace user:user with your main user name and set the right path ..[/COLOR]

---

### Post by DrScum on 2009-08-30
Thanks to all of your help. I got it fixed with the suggestions made here.

---

