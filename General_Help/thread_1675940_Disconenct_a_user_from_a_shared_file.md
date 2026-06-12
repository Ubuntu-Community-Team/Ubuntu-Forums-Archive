---
title: "Disconenct a user from a shared file"
date: 2011-01-26
forum: General Help
---

### Post by burnleyhome on 2011-01-26
I moved my file server from Windows 2000 to Ubuntu. Everything is great and works a treat.
We use a front-end/back-end Access database (back-end resides on the server) and when the database is in use a lock-file is created. Sometimes if the client crashes (it is Windows afterall), the lock-file remains and stops all users from accessing the database.

In Windows I could see all the people that were accessing open files and close the file from the server.

For my limited knowledge I view the open files in the directory
sudo lsof +D <directory>
but how do I disconnect the user from them (apart from revoking their shared privilages and then restoring them)?

Cheers for the help in advance.

---

