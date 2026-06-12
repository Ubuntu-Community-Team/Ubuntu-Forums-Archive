---
title: "User Permissions?"
date: 2010-04-15
forum: General Help
---

### Post by kla0005 on 2010-04-15
Hey guys,

I have added a new user on my ubuntu server, and done so when he logs on sftp, he' starts in the folder belongs to him, wich is:
/var/www/declan/ <-- the declan folder.

But, for some reson he still can go a root back? How can i do se he cant leave the declan folder.. He may enter new folders that he has created in his declan folder ofc. but how can i do so he cant go a step longer back than hes own declan folder. He may not enter www folder?

Hope you guys understands my question :)

Hope u can help me.

---

### Post by dominiquec on 2010-04-15
What you want to do is chroot for the FTP server.

Try this thread: [http://ubuntuforums.org/showthread.php?t=379010](http://ubuntuforums.org/showthread.php?t=379010)

---

