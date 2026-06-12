---
title: "Change User Privileges"
date: 2009-08-23
forum: General Help
---

### Post by crookedj0k3r on 2009-08-23
Okay, I've reinstalled Ubuntu 9.04 for the 6th time trying to fix this.

It started when I tried to move a new theme to my usr/share/themes folder, it said I did not have permission to do so, so I furthered my research into the matter that I did not have complete control over my OS.

I went to the properties of the share/themes folder and it says under the permissions tab "You are not the owner, so you cannot change these permissions"

How do I put my user as the owner of the computer, thus giving me complete control over my system entitling me the privilege of ruining it any way that I want?!

Thanks, 

crook.

---

### Post by j7%&lt;RmUg on 2009-08-23
You are only the owner of your /home/USERNAME directory.

The owner of /usr/share/themes is root.

So to put a theme there you should do it with the terminal and enter the root password.

Type these commands in order:

```

cd /path/to/theme/you/wish/to/move
cp fileyouwishtomove /location/you/want/to/move/it/to

```

It should then ask you for your password.

Your root password is usually the same as your login password.

---

