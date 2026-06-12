---
title: "NTFS trash folder for more than one user"
date: 2010-08-08
forum: General Help
---

### Post by ItalOz on 2010-08-08
Hi,

I am breaking my head on this. I recently added another user to my system. My principal user has ID=1000 the new user has ID=1001, they both belong to the group id 1000.

I have an NTFS partition that I am now able to mount for both the users at boot with this line in the fstab:
```
UUID=F472BDC372BD8ABE /media/OS ntfs-3g quiet,defaults,uid=1000,rw,utf8 0 0
```

The point is that if I don't put the option
```
uid=1000
```
I cannot move files to trash but only delete them
if I put it I can move files to trash but only if I am logged in as the user with ID=1000
I have tried to change the option and use the groups logic instead of the users (groups are there for this purpose aren't them?) and change the option into
```
uid=1000
```
since both the users belong to group 1000
but the result is that in this way none of them can trash anything (only delete permanently)
I have also tried to create a .Trash-1001 folder did not work either

Is there a way to be able to use a Trash folder (or different trash folders I don't mind) and be able to trash files for different users in NTFS?

And if yes how the fstab line would look like?

THANKS!

---

### Post by dino99 on 2010-08-08
Dont break your head now [-o< you'll need it later  #-o

use mountmanager to deal with partitions and devices (system admin mountmanager)

---

### Post by ItalOz on 2010-08-08
Thanks for caring mate :D
I will surely try mount manager but I really wanted also to understand the reasons.

Furthermore I think that mount manager will write some modifications to fstab right? I might read it from there (if it does not messes it up too much)

does any one know how to write the proper options?

great forum!

---

