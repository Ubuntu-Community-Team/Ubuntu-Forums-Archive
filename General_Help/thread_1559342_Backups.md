---
title: "Backups"
date: 2010-08-23
forum: General Help
---

### Post by Monotoko on 2010-08-23
Hi there,

I would like to use a bash script to package some server backups every day, then connect to my home system and push the backups through.

How would you guys advise doing this? FTP seems like a good option but I am not sure how to use it in a bash script to connect and push the files through. As the home system is not going to be up 24/7, how can I get the script to check if it is there before trying to connect?

Thank you :)

---

### Post by martin_legion on 2010-08-23
Check this tutorial, it might help:

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)

---

### Post by terdon on 2010-08-24
Hi, you could just write your script to first ping the remote machine, and if that gives a response (if the remote server is up) then copy your files.

Also, have a look at the pscp program. It lets you give the password on the command line which is useful if you want to automate the process.

post back here if you need help with the scripting.

---

