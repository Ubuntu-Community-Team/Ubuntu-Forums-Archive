---
title: "When unpacking a tar using sudo, it creates everything with a co-workers username"
date: 2010-11-05
forum: General Help
---

### Post by RugerRedhawk on 2010-11-05
Ok, so myself and a co-worker are both in the group root, and both in the sudoers list. When I log in as myself. Upload a tar file using filezilla logged in as myself. Then unpack the file using the 'tar' command, it creates the new folder and every file it unpacks is listed with my co-worker's username listed as the owner and his group as the group. 

If I use sudo to create files any other way, 'root' is the owner and group. This is what I would expect. 

There is a thread about this in the archive, marked as 'solved', yet it was never solved the guy just decided to not use sudo. Of course I have a workaround where I can do chown and chgrp, but there is definitely something messed up going on there. I'm running Ubuntu Server 10.04.1 .

Here is the old thread: [http://ubuntuforums.org/showthread.php?t=545020](http://ubuntuforums.org/showthread.php?t=545020)

---

### Post by CharlesA on 2010-11-05
tar can retain permissions if you tell it to.

Check out the man page:

```
man tar
```

---

### Post by RugerRedhawk on 2010-11-05
> **CharlesA said:**
> tar can retain permissions if you tell it to.

Check out the man page:

```
man tar
```

So I see this in the man page: > -p, --preserve-permissions, --same-permissions
           extract information about file permissions (default for superuser)


but guess I don't fully understand. If my username is userA and I upload a tar file, and run tar on it, why would everything it unpacks have an owner of userB? I would think that root would be the owner.

---

### Post by CharlesA on 2010-11-05
I don't know why you'd untar something as root, unless you wanted to preserve the permissions.

If you are logged in as userB and unpack the tar, the files will be owned by userB. If you are logged in as userA and untar the files, they will be owned by userA.

---

### Post by herta on 2010-11-05
Use "tar xpf tar-file.tar" to **p**reserve permissions and "ownership". 

If copying a tar file from another system, make sure that uid's of the accounts are the same.

---

### Post by RugerRedhawk on 2010-11-05
Interesting. I uploaded the file from a windows machine. My username is shown as the owner of the .tar file after the upload. When I run sudo tar it changes the owner of all the extracted files to a completely different user who has never owned the tar. The reason I was using sudo was so that the owner and group were 'root', just makes it easier because then anybody in the 'root' group (which we both are) can access it more easily. 

Not a huge deal, it just seems very peculiar to me. Could there be a userid stored inside the tar from the person who initially created the .tar file which is then being used when I unpack it? I downloaded this tar from online.

---

### Post by herta on 2010-11-05
The permissions and ownerships are not those of the tar file, but of the files in the tar file.  (Just think about this.  This used to be the way to run backups.  It wouldn't work very well if you could only restore the files as belonging to the account who untar'd the tar file.

Try "tar tvf tar-file.tar" to view what permissions and ownerships are on the files in the tar file.

---

### Post by RugerRedhawk on 2010-11-05
> **herta said:**
> The permissions and ownerships are not those of the tar file, but of the files in the tar file.  (Just think about this.  This used to be the way to run backups.  It wouldn't work very well if you could only restore the files as belonging to the account who untar'd the tar file.

Try "tar tvf tar-file.tar" to view what permissions and ownerships are on the files in the tar file.

Yeah when I run "tar tvf" it lists a username not on our system, obviously the creator of the tar file at the company who made it. It must be that he has a userid that somehow is the same as the userid for userB on my system then?  I guess at least that clears up why this might be happenening.

---

### Post by herta on 2010-11-05
> **RugerRedhawk said:**
> Yeah when I run "tar tvf" it lists a username not on our system, obviously the creator of the tar file at the company who made it. It must be that he has a userid that somehow is the same as the userid for userB on my system then?

That's correct.  The file owner is stored as a numeric uid, which is translated against the current system's /etc/passwd.  If there is no matching uid, it will just show the uid number.  Otherwise it shows the name of your local account.

It's one of the reasons why I keep the same uid/gid for all acounts on all servers.

---

### Post by RugerRedhawk on 2010-11-05
> **herta said:**
> That's correct.  The file owner is stored as a numeric uid, which is translated against the current system's /etc/passwd.  If there is no matching uid, it will just show the uid number.  Otherwise it shows the name of your local account.

It's one of the reasons why I keep the same uid/gid for all acounts on all servers.

Ok, thanks for clearing it up, I had no idea what was going on.

---

