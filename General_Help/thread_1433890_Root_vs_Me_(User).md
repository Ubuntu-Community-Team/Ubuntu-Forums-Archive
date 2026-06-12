---
title: "Root vs Me (User)"
date: 2010-03-19
forum: General Help
---

### Post by Si2100 on 2010-03-19
I;ve jsut installed Linux Ubuntu 9.10, and found that i cant edit the files on my C driver as i comes up saying " Error: You do not own these files"

Even though i have given myself all Root/Admin control it still say it?
what can i do to take be come the admin without deleting my account or root account?

---

### Post by da burger on 2010-03-19
Prefix the command with ```
sudo
``` then type in your password (you won't see any letters not even asterisks).

eg ```
sudo apt-get install package
```

If the command is graphical use gksudo instead.

---

### Post by mridkash on 2010-03-19
You need to open files as root, root account is disabled by default on Ubuntu.

open terminal
applications > accessories > terminal

and write this command

sudo nautilus

then enter your password

now the file manager opens as root and you can edit any file.

---

### Post by nikhilbhardwaj on 2010-03-19
you may want to write an fstab entry for your windows partition

---

### Post by eriktheblu on 2010-03-19
Am I understanding that you have a dual boot system (MS Windows and Ubuntu) and you are trying to access files in your windows partition?

If so, where is the partition mounted?

I expect sudo chown would do the trick.

---

### Post by nikhilbhardwaj on 2010-03-19
> **mridkash said:**
> You need to open files as root, root account is disabled by default on Ubuntu.

open terminal
applications > accessories > terminal

and write this command

sudo nautilus

then enter your password

now the file manager opens as root and you can edit any file.

in my view it is not the best practice to open nautilus or any file manager as root
a user might accidentally delete files.
setting the correct permissions is a better approach

---

### Post by Seq on 2010-03-19
> **mridkash said:**
> sudo nautilus

**Don't do this**. sudo can cause problems when using GUI applications. Use gksu instead:

```
gksu nautilus
```

You can also run this from the "Run" dialog. Press ALT+F2 to summon it.

As a more general question to the original poster: What are you trying to do exactly. Note that a lot of changes to certain parts of the system will be silently overwritten by updates.

---

### Post by oldos2er on 2010-03-19
> **eriktheblu said:**
> Am I understanding that you have a dual boot system (MS Windows and Ubuntu) and you are trying to access files in your windows partition?

If so, where is the partition mounted?

I expect sudo chown would do the trick.

 Chown won't work on an NTFS partition. The OP needs to create an entry for the partition in /etc/fstab. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Iowan on 2010-03-19
Just a couple of links to reiterate what's already been said:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")
[graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Si2100 on 2010-03-23
thanx, guys

i did have it on a partiton unless i gave up and formated. but i might try agin soon

---

