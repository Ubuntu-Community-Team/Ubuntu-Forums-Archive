---
title: "Lost ownership and permissions"
date: 2010-10-22
forum: General Help
---

### Post by htcoles on 2010-10-22
I seem to have lost ownership and permissions for all my files.  I noticed that my torrents had stopped downloading with a permission denied error, then noticed that I wouldn't delete files, sure enough I couldn't even create files or edit text documents (code::blocks wouldn't let me save my project, text docs would only open as read-only).

I retraced what I had done in the hour or so before this, and the only possible thing that could have gone wrong is that I installed emacs, then xemacs, both using apt-get, then removed xemacs, then ran autoremove, followed by update and upgrade.

As a cheap workaround, I chown'd the / dir, since I had some stuff to do that couldn't wait, but some things such as transmission won't work, and I still can't edit directories in my home dir.

Any help or suggestions would be greatly appriciated

---

### Post by blueridgedog on 2010-10-22
In my experience chown'ing / is fatal.  You should have done a recursive chown of /home/USER where your user account is user:
```

cd /home/user
sudo chown -R user:user .
```

---

### Post by bagatonovic on 2010-10-22
If the above suggestion gives you errors, simply put sudo in front of the command:

sudo chown -R username:groupname /path/to/home/folder

---

### Post by htcoles on 2010-10-22
worked like a charm, thanks a lot for the help

---

