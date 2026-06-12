---
title: "Permissions Others"
date: 2011-04-22
forum: General Help
---

### Post by xtra123 on 2011-04-22
Hi @ll,

I've created a new user for a SSH tunnel only.

After login I can access all directories because permissions is set for "Others" to "Access files".

Now my question: Is this normal that permissions for Folder access for "Others" is always set to "Access files"?

I don't want my SSH tunnel user accessing the directories.

Can anyone please show me how to secure this? :confused:

---

### Post by SavageWolf on 2011-04-22
I have no idea why Ubuntu is set up like that...

To have all new files created not be readable to others, add "umask 007" to ~/.bashrc.

To change all the files currently to those permissions, unmount any FTP places and run "chmod -R o-r ~/".

---

### Post by xtra123 on 2011-04-22
Is this permission set in your installation of Ubuntu too?

I mean the whole "/" is at least readable to "Others".

---

### Post by Lars Noodén on 2011-04-22
> **xtra123 said:**
> 

I don't want my SSH tunnel user accessing the directories.



You'll want OpenSSH set up to chroot that account.  Chroot will lock it into a single subdirectory.

The configuration directive to look for is [ChrootDirectory](http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config)

---

### Post by xtra123 on 2011-04-22
Great! Seems exactly what I was looking for.

Thank you very much! :)

---

