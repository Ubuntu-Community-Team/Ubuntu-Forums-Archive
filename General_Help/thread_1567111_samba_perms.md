---
title: "samba perms"
date: 2010-09-03
forum: General Help
---

### Post by davidstoll on 2010-09-03
I've seen quite a few postings about how to mount samba shares in fstab, but I just can't seem to get the perms to anything other than rwx-r__-r__ root:root

I would like them to be something else (depending on what I'm trying to mount) and also my normal username rather than root.

I'm mounting a Windows samba share.  It doesn't require login credentials.

So, I'm looking for the fstab entry that gives me all the options to set and change the user and perms.

Thanks so much!

---

### Post by KeyserSoze93 on 2010-09-03
try adding the option uid=1000 (or whatever your uid is.)

Likewise gid for your group.

I think you can also use your actual username there too, like:

uid=bob,gid=bob

Example:

```

//DECAL/theo /media/decal smbfs users,noauto,iocharset=utf8,directio,uid=theo,gid=theo,file_mode=0770,dir_mode=0770 0 0

```

Change auto/noauto if you need to. file_mode and dir_mode should also be pretty obvious.

---

### Post by davidstoll on 2010-09-03
> **KeyserSoze93 said:**
> try adding the option uid=1000 (or whatever your uid is.)

Likewise gid for your group.

I think you can also use your actual username there too, like:

uid=bob,gid=bob

Example:

```

//DECAL/theo /media/decal smbfs users,noauto,iocharset=utf8,directio,uid=theo,gid=theo,file_mode=0770,dir_mode=0770 0 0

```

Change auto/noauto if you need to. file_mode and dir_mode should also be pretty obvious.


Using these settings, I get...
drwxr-xr-x 1 root root
for all files and folders after I "sudo mount -a".
I'm not sure what the auto, noauto does.
I also tried cifs and smbfs.

---

### Post by davidstoll on 2010-09-08
> **davidstoll said:**
> Using these settings, I get...
drwxr-xr-x 1 root root
for all files and folders after I "sudo mount -a".
I'm not sure what the auto, noauto does.
I also tried cifs and smbfs.

Any ideas why the mounting creds don't match what I'm putting in the fstab mount line?

---

### Post by KeyserSoze93 on 2010-10-01
> **davidstoll said:**
> Any ideas why the mounting creds don't match what I'm putting in the fstab mount line?

Try mounting it yourself. i.e. "mount /media/blah" as your own user.

auto / noauto selects whether the filesystem is mounted when you turn the computer on, see the man page for fstab

---

### Post by davidstoll on 2010-10-01
Here is what seems to have fixed it, maybe someone else can give a better explanation...

If the shared network folder (in my case a Vista share) does not have "Guest" as one of the "people to share with", then when you mount, it gets mounted as 777 root:root....strange.

In Vista, I had Administrators, [my user name] and Everyone listed as people with access.  However "guest" was not in that list.  As soon as I added that, fstab behaved as I would have expected.

So, it was probably more of a windows issue than ubuntu, but I'm not sure why.

---

