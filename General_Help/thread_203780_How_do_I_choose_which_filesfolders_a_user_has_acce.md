---
title: "How do I choose which files/folders a user has access to?"
date: 2006-06-25
forum: General Help
---

### Post by zazery on 2006-06-25
I recently installed phpmyadmin and noticed the config.inc.php file contains my mysql password in plain text. My .htaccess file prevents the file from being viewed from a web request, however it does not stop a user logged in via ssh to view the file. After playing around with permissions it seems like in order for the file to work with phpmyadmin it must be readable by others. There may be other files that I don't want the user to access as well.

The account I'm trying to create only needs access to some folders. I am wondering how I can basically pick and choose which folders and files I would like to give the user access to.

've tried to look around on the internet and on the forums and haven't found what I'm looking for. Any help would be greatly appreciated.

Thanks.

---

### Post by Zikes on 2006-06-26
Right-click on the file and go to Permissions.  Make sure you're the owner, then set it so that it is not readable by other users.

---

### Post by zazery on 2006-06-26
[QUOTE=Zikes]Right-click on the file and go to Permissions.  Make sure you're the owner, then set it so that it is not readable by other users.[/QUOTE]
Thanks for the reply. Yes that's what I'm doing with my home directory.  However, as stated in my first post in order for phpmyadmin to function it must be readable by others, otherwise it will give me an error that it can't read the config file when accessing my phpmyadmin setup.

I have read somewhere the I can "jail" a user to a certain directory such that they won't be able to go higher than that directory. However, I'm looking to also include a few folders outside the desired jail space.

Thanks.

---

