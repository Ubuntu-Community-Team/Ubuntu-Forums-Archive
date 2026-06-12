---
title: "LAMP server &quot;forbidden&quot; and home folder access"
date: 2010-09-24
forum: General Help
---

### Post by Findarato on 2010-09-24
Hello,

I am not new to Ubuntu, and have installed LAMP with all the versions up from 7.04 . Every time I do this, I set it up so that the www directory actually serves-up my Dropbox folder.

Instead of doing this by actually changing the apache directory, I simply put in a symlink from the WWW directory.

This worked many times, but today, under Maverick, I got the following error : 
"Forbidden You don't have permission to access / on this server."

I spent a LOT of time on the web trying to solve this error and in the end, it got solved simply by enabling permissions "access" to "others" direclty on my home folder (because my Dropbox folder is, of course, within my home folder).

However, I have no idea if this is a good idea. Does this mean that simply anyone could access any file on my computer ??

Alternatively, does anyone know how I could proceed to make this LAMP server work WITHOUT having to change my Home directy permissions this way ?

Thank you very much for your help,

Joshua

---

### Post by Findarato on 2010-09-25
Any help here ? :)

---

