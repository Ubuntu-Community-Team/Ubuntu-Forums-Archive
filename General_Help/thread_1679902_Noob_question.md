---
title: "Noob question"
date: 2011-02-01
forum: General Help
---

### Post by Bob Hansen on 2011-02-01
I have been trying to find an answer to this problem using Google, but with no luck.

I have installed Ubuntu Server and Open SSH on the server. I can connect to the server using Bitvise Tunnelier. The problem is I can only transfer files to my home directory. I have installed L4D on the server in /home/l4d, but cannot transfer files. Permission denied. How can I transfer files to l4d and all its subfolders?

Thank you for your help

/bob

---

### Post by Joe of loath on 2011-02-01
As a user, you only have permissions to alter your home directory, /home/user. To transfer files to a folder outside of this, you will have to use sudo to perform the commands as root, or put the folder in your home directory.

---

