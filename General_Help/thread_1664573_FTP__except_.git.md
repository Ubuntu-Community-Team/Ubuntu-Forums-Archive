---
title: "FTP * except .git"
date: 2011-01-11
forum: General Help
---

### Post by Alan James on 2011-01-11
I am trying to backup my entire workspace directory to a remote server and I want to exclude the .git directory located within the folder. I back up this directory every few hours so I have written a script that FTPs all the contents of the directory to the online server, however I don't know how to exclude the .git directory. I have attached a tar containing the script (with generic server information) so you can see what I am doing so far.

How do I stop it from uploading the .git directory, while still uploading everything else?

---

### Post by Alan James on 2011-01-11
Anyone have any suggestions?

---

### Post by asmoore82 on 2011-01-11
I would avoid old fashioned FTP at all costs.
Especially if data will be transmitted across the wide Internet.

It is trivially easy to retrieve username/password data from an unencrypted FTP data stream.

The absolute best solution for this situation would be rsync.
It provides blazing efficient data backups especially if an older copy
of the data already exists in the remote location.

It also has the file filtering features that you require and uses SSH encrypted traffic by default.
If you control the remote backup server, you don't even have to install and configure an rsync server.
You simply allow Secure OpenSSH login and have the rsync binaries available.

I believe rsync is installed on Ubuntu by default, but there is also a great GUI available: Grsync.

---

