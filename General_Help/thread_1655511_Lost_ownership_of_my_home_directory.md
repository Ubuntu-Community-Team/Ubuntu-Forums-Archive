---
title: "Lost ownership of my home directory"
date: 2010-12-29
forum: General Help
---

### Post by didix_1 on 2010-12-29
Hello,
I have lost ownership of all my home directory.
I have installed redhat 6 and mount same home directory of Ubuntu and i have created a user with same username.
All was ok until i rebooted and went into Ubuntu i couldn't login.
I had an error about .ICEauthority, i could own that file in my home directory and all hidden file by using chown marc /home/marc/.* and then logged in. I still doesn't own all my files and folders.
I there a simple way to re-own all files and folders or i have to chown them one by one XD
:confused:
I tried chown marc /home/marc/*/*/*/* it worked but if i add one more * i get "argument too long"
Thank you.

---

### Post by MDguy on 2010-12-29
try:
```
sudo chown marc -R /home/marc/*
```The R means recursive, which means it will go to every subdirectory.

---

### Post by hawkmage on 2010-12-29
If I remember correctly Ubuntu starts UIDs at 1000 and RedHat at 500.  So even if you accoung has the same name it is the UID/GID that Linux uses for permission/ownership not the account name.

You will have to find out what the "BAD" and "Good" UID and GIDs are.  Let's assume that the BAD UID and GID are 500 and 501 while the "Good" UID and GID are 1000 and 1001.  (Remember these are example numbers)

To fix the UIDs run the command:
```
sudo find / -uid 500 -exec chown 1000 "{}" \;
```
To fix the GIDs run the command:
```
sudo find / -gid 501 -exec chgrp 1001 "{}" \;
```
I do this in two commands just incase there are any files that don't have both the user and group set incorrectly.

I have used this process to fix permissions on files when having to change a users UID and GID

---

### Post by coffeecat on 2010-12-29
> **didix_1 said:**
> I have installed redhat 6 and mount same home directory of Ubuntu and i have created a user with same username.

Using the same username was probably the problem. If RedHat behaves like Fedora (which it probably will) it will make the UID (user ID) of the first account 500, whereas in Ubuntu it is 1000. Whether it overwrote all your original home folder and contents, or recursively changed the UID of existing ones is a moot point. Once you've finished recursively chowning everything in Ubuntu, you may find that you can't access your personal 'marc' files in Red Hat.

When you use chown, although it refers to a username, the actual file ownership uses the UID.

---

### Post by didix_1 on 2010-12-29
Yes I just noticed that the UID was 500 in redhat, anyway thank you very much all for your help problem solved the recursive chown worked :)

---

