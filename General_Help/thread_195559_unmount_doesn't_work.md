---
title: "unmount doesn't work"
date: 2006-06-13
forum: General Help
---

### Post by User-007 on 2006-06-13
Hi,

Where is my unmount command?

@a81-197-218-65:~$ sudo unmount /mnt/win_f/
sudo: unmount: command not found

Same occurs when trying as non-root user.

@a81-197-218-65:~$ unmount /mnt/win_f/
bash: unmount: command not found

Can this occur because of modifying sudoers by this way: [http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password)

I will appreciate your help.

Thanks
User JB

---

### Post by DoktorSeven on 2006-06-13
Command is **umount**, not unmount (no 'n' after the u).

---

### Post by User-007 on 2006-06-13
Oh, I dummy. Thanks.

---

### Post by mumushi on 2006-06-13
[QUOTE=User-007]Oh, I dummy. Thanks.[/QUOTE]

its ok everybody commits mistakes ;)

---

### Post by HAARP on 2006-07-17
Sorry for digging this old thread up, but I've got a short question:
I tried creating a bash script to get the right **unmount** command, like this:

/bin/unmount
```
#!/bin/sh
umount
```

But how do I give umount it the command line arguments used to start **unmount**?

---

### Post by MacMan on 2006-07-17
> **HAARP said:**
> But how do I give umount it the command line arguments used to start **unmount**?

I don't know if I understand correctly what you want to do, but if you want to create a synonym of umount called *unmount*, you could just type something like this in a console:

```
$ alias unmount=umount
```

Ciao.
-- 
MacMan

---

### Post by HAARP on 2006-07-17
Well, I tried that. Problem is, to unmount something, you need root rights. So I'd need to **sudo** the command
But aliases are only for the user who makes them, and **sudo alias** won't work :-? 



..do aliases and enviroment varables stay when rebooting and such?

---

### Post by MacMan on 2006-07-18
> **HAARP said:**
> ..do aliases and enviroment varables stay when rebooting and such?

No, they don't. If you want them to stay, you have to add them to your bash profile.

To make them permanent for one user only, you add them to the file .bashrc in the user's home directory. If you want the change to apply for all the system's users, you should change /etc/bash.bashrc .

As for the unmount alias, you could use something like:
```
alias unmount="sudo umount"
```

You can also set up sudo so that a command doesn't need the user's password to execute with superuser privileges. If safety isn't a big concern to you, you could give this option a try.
To do this, you need to change the sudoers configuration file. You do this by using the command
```
sudo visudo
```
But first you want to read the sudoers man file:
```
man sudoers
```
It's not difficult if you read the man page and especially the examples, but if you need a hand just ask.

I hope this helps.

Ciao.
-- 
MacMan

---

### Post by HAARP on 2006-07-18
I didnt't know about the .bashrc.

I settled with just a symlink to umount named unmount. Much easier :) 
In my opinion, symlinks are the best thing since the creation of filesystems. gud stuff!

Thanks anyway.

---

### Post by DoktorSeven on 2006-07-18
for future reference:
[b]
#!/bin/bash
umount "$@"
[/b]
does what you wanted.

---

### Post by HAARP on 2006-07-18
Thanks.

---

