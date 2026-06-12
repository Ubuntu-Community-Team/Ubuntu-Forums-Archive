---
title: "Help in Repairing Nautilus Configuration permissions"
date: 2006-05-14
forum: General Help
---

### Post by whittwuli on 2006-05-14
I told a friend for a quick fix to access his external hard drive to run Nautilus as root.  He did this by getting root prompt in terminal and then typing nautilus on the command line.

Once I had time I had him fix the Hard drive right thru /etc/fstab.

He now gets this error:

Nautilus could not create the required folder "/home/tim/Desktop".
Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

Is this because some nautilus configurations are now root? 

No desktop icons show up for him and he gets this error on every boot up and every time he opens Nautilus.

How can I fix this problem for him?

---

### Post by Ramses de Norre on 2006-05-14
Does mkdir /home/tim/Desktop work?
Check the permissions of the home folder otherwise. (should be owned by the user with rwx for owner)

---

### Post by whittwuli on 2006-05-16
Thanks for the reply.

This did work, however wasn't as straight forward.

There was a symbolic link Decktop -> /home/tim/Desktop ...

But the folder did not exist.  So I deleted the symbolic link and mkdir /home/tim/Desktop.

Everything is working like a champ now.

Cheers!

---

