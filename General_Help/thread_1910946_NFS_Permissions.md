---
title: "NFS Permissions"
date: 2012-01-18
forum: General Help
---

### Post by Valpskott on 2012-01-18
I've got a weird situation at home. I have a NFS export on my server. This morning I connected to it from my computer via NFS, I changed permissions via ssh(as root) with "chmod -R 666" on a directory of movies, and now only root can access that directory even though "ls -l" lists the directory as belonging to my user and my group (johan:johan) and having "rw rw rw".

I've also checked the UID and GID, which both are 1000. The same UID and GID is used on my computer, as is the same names for those *IDs.

The other directories are also listed as belonging to johan:johan, and I can access those directories just fine.

What could be causing this?

---

### Post by mcduck on 2012-01-18
So these permissions were set for the directory itself, not it's contents?

You need execute permission to be able to access a directory and it's contents (while read permission on the other hand defines if you are allowed to view the contents or not).

---

### Post by Valpskott on 2012-01-18
> **mcduck said:**
> So these permissions were set for the directory itself, not it's contents?

You need execute permission to be able to access a directory and it's contents (while read permission on the other hand defines if you are allowed to view the contents or not).

My understanding is that the -R flag I used means it was done recursivly (the directory and all content in the directory).

Anyway, I just tried setting chmod 666 on a directory on my work computer and same result... then made the directory executable again, seems to be working.. rookie mistake. Thanks a bunch!

Funny thing is that I'm able to open the directory if I am root.

---

### Post by mcduck on 2012-01-18
Well, root of course has the ability to do anything on a Linux system, so such permissions are not a restriction for root user.

(even the possibility of restricting root from accessing a directory through permissions wouldn't make sense, as root would be able to set the permissions (or even ownership) to whatever he wants anyway. The execute permission on a file would be a different case, as it's purpose is not only tho restrict other user's access to the file, but also to serve as a confirmation that the owner of the file really wants it to be executable)

---

### Post by Morbius1 on 2012-01-18
Excuse the interruption but this will not work:
> I changed permissions via ssh(as root) with "chmod -R 666" on a directory of movies,You need the "execute bit" turned on for a directory so that you can open it to see what's inside. But you don't want to do a "chmod -R 777" either since that will make every file executable as well. So what I recommend is this:
```
chmod -R a+rwX /path-to-folder
```All folders will be 777 and  all files will be 666 except those that were executable to begin with.

---

