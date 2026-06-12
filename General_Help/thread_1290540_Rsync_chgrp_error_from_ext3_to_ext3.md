---
title: "Rsync chgrp error from ext3 to ext3"
date: 2009-10-13
forum: General Help
---

### Post by skelooth on 2009-10-13
Hello, I'm using rsync to make a backup of a website, but I'm getting chgrp errors

I'm using the line:
rsync -a --delete [email]root@mysite.com[/email]:/var/www /mnt/backups/mysite.com

where the mnt/backups is a CIFS mounted ext3 share from an NAS running a very stripped down linux. The file systems on all three machines involved is ext3. Is this a problem with CIFS? Is there a work around? I need to maintain groups/permissions.

Thank you in advance for any help you can offer.

---

### Post by StuartN on 2009-10-13
> **skelooth said:**
> rsync -a --delete [email]root@mysite.com[/email]:/var/www /mnt/backups/mysite.com

I guess that /mnt/backups should belong to you and the local path exported as /mnt/backups should belong to the account you are connecting as in your mount command. For instance my local path (within the NAS) is /mnt/disk1/me/my_back_up/ and belonged to root as created by the NAS software, which let me copy files but not change permissions, times etc.

Alternatively you could start rsyncd on the NAS and then rsync without mounting, so you have only the permissions of the rsync module on the NAS to correct.

---

### Post by skelooth on 2009-10-14
Hmmm, I tried changing ownership but it didn't help, now it also gives me errors that chown failed :) It is maintaining permissions though, so perhaps I should just be grateful it works as much as it does. It just doesn't retain the owner information, which chown -R www-data * would fix if need be. I guess. :shrugz:

---

### Post by StuartN on 2009-10-14
> **skelooth said:**
> Hmmm, I tried changing ownership but it didn't help, now it also gives me errors that chown failed :)

That is a sign your doing the right thing, if only you get the right parameters. For my system I have the following:

~/Mountpoint is a directory with rw access belonging to me and I  mount the NAS with:

```
sudo mount -t cifs -o username=NasUser,password=NasUserPassword,uid=UbuntuUser,gid=UbuntuGroup, NAS:/NasUserPath ~/Mountpoint
```

Where NasUser is an account on the NAS and is the owner of the path referenced by NasUserShare. UbuntuUser / Group is my local (desktop) account and the owner of ~/Mountpoint.

When I rsync I use my own account, not sudo:

```
rsync -avh --delete ~/Documents/ ~/Mountpoint/Documents/
```

So I am running the command, I own ~/Documents and I am copying to a location mounted by me using my NasUser account.

---

