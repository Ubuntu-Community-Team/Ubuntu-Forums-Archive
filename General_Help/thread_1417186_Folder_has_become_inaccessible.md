---
title: "Folder has become inaccessible"
date: 2010-02-27
forum: General Help
---

### Post by terminalmancer on 2010-02-27
I'm sure there have been dozens of posts by stupid newbies (like myself) about this but I have no idea how to find any of the answers. I apologize in advance.

I SSH-ed into my webserver and discovered that the user I was logged in as had no permissions for the www folder. I attempted to fix this by adding a group to this user (group "web") and then changing the owner of the www folder to "web".

Now, the folder is inaccessible to any and everything. I cannot view it. "sudo cd [folder]" is apparently an invalid command. Insofar as I can tell, I have returned the permissions of the folder to what they used to be... but I still can't get into the folder. How do I fix this disaster? I need to get those files back if at all possible. :(

---

### Post by stlsaint on 2010-02-27
is that user you are logged in as part of the admin group? 
you can use the chown command to give yourself permissions.
 Try this on the webserver:```
chown -R www-data:www-data /var/www/
```

---

### Post by terminalmancer on 2010-02-27
> **stlsaint said:**
> is that user you are logged in as part of the admin group? 
you can use the chown command to give yourself permissions.
 Try this on the webserver:```
chown -R www-data:www-data /var/www/
```

Thanks for the advice. Yeah, the user was, and was still unable to access the directory.

I am not entirely sure what happened. I went to bed last night unable to access the directory, and when I woke up this morning I was able to. Perhaps something in the security settings was cached? I'm confounded, but it works now.

---

