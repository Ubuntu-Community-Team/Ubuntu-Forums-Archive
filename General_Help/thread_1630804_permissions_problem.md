---
title: "permissions problem"
date: 2010-11-25
forum: General Help
---

### Post by vys on 2010-11-25
hello. I'm using lucid lynx, and I'm an experienced ubuntu user, but I've encountered a problem. the permissions for my home directory were accidentally changed from 'access files' to 'create and delete files', and I changed them back, but ever since then I am not able to change any preferences/settings at all. power management, themes, panels, emerald, anything. my user account is supposed to be the administrator, and all the user privliges are checked. can someone tell me how to get control of my computer back?

---

### Post by 73ckn797 on 2010-11-25
Open a terminal and enter:
```
sudo chown -R yourname:yourname /yourname/home
```

Substituting yourname for whatever is the name, such as Ubuntu:john. This should give permission throughout all folders in the /home folder.

---

### Post by sikander3786 on 2010-11-25
> the permissions for my home directory were accidentally changed from 'access files' to 'create and delete files

For Your home directory, you need to be owner of that directory and free to create or delete any files in there.

I think there was no problem until you changed that to 'access files' yourself.

Hope you can change them back yourself ;-)

---

### Post by vys on 2010-11-25
thanks for the help. I tried running that command, and I was denied permission to /home/myname/.gvfs. do I have to be the root user?

---

### Post by sikander3786 on 2010-11-25
Putting in sudo gives you temporary root access so thats not the issue here.

.gvfs seemed to create problems ever since it was included in Gnome.

The best workaround I can think of is to try removing .gvfs as there seems to be no apparent solution to that, at least to me.

```
rm -r /home/[username]/.gvfs
```

And then again try chown.

You can wait for the consensus to be developed on this though.

---

### Post by vys on 2010-11-25
what does .gvfs do?

---

### Post by WorMzy on 2010-11-25
That folder is a bit of an exception, don't worry about it. You would have needed to use sudo if you weren't already the owner, but since you didn't get any other error messages, your files must be correctly owned already.

That suggests that the permissions are to blame.

Open a terminal and run:

```
chmod -R ug+rwx ~
```

---

### Post by 73ckn797 on 2010-11-25
.gvfs in my /home has nothing in it so that should not be any issue if your's is also empty.

---

### Post by Morbius1 on 2010-11-25
Um ..... .gvfs is where Nautilus mounts remote Samba shares when you browse and connect to the Network.

---

### Post by vys on 2010-11-25
I'm going to assume it was that last command that did it, but on a whim I restarted my computer and now everything works. thanks a million, you guys. I was considering a re-install.

---

### Post by 73ckn797 on 2010-11-25
Glad all is working now.

Here is a good link for future solution searches:
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)
It has been the source for many solutions that I have had.

---

