---
title: "Can't login after file system downgrade"
date: 2009-12-22
forum: General Help
---

### Post by ilerdl on 2009-12-22
I'm running ubuntu 9.10 on a Dell GX-270 Optiplex with 2GB RAM.

I had my home partition formatted for ext4.  I backed it up with rsync -a and put a new ext3 file system on it.  I looked up UUID from blkid and put that in /etc/fstab, and changed type to ext3.  Then I restored the files using rsync -a.  All this was done under system rescue cd 1.3.3.

However, when I rebooted, my home partition won't mount, nautilus won't run, and I'm kind of stuck.

Any suggestions?

Cordially,


Dave

---

### Post by ilerdl on 2009-12-22
Evidently the home partition is mounting correctly.  All the data is there.

I rebooted to system rescue cd and copied my home directory from backup to /opt/iler, then edited /etc/passwd and set the home directory from /home/iler to /opt/iler.

Now I can login, but still can't login when /home/iler is the default login directory for my account.

When logging in, I get the following error messages:

Cannot update ICEauthority file /home/iler/ICEauthority

and

There is a problem with the configuration server.  (/usr/lib/libgconf2-4 exited with status 256.

, and there was one more about Nautilus not being able to run.

So how do I now get /home back into production?

Cordially,



Dave

---

### Post by ilerdl on 2009-12-22
Sorry to bother the forum.

Problem of not being able to login was caused my a stupid faux-pas on my part.

When I restored my data to the /home partition, I did it to the home directory.

The path to my login directory was therefore, /home/home/iler, which differed from the login directory of /etc/passwd.

Things are set back right, and I apologize for the posts.

---

