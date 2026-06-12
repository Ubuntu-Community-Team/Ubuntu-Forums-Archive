---
title: "cannot create files in symlinked dir"
date: 2010-03-04
forum: General Help
---

### Post by pkkelly on 2010-03-04
Hi everyone

I'm having difficulty with ubuntu's sym links just now as I have a remotely mounted disk on another ubuntu system which the first system connects to via an fstab entry something like this:

//192.168.1.151/share /mnt/overspill smbfs guest,_netdav	0 0

the /data folder on the first machine (141) is shared via samba and contains a soft symlink called ARCHIVE linking to /mnt/overspill

now when I go into the /data share via samba (or even via terminal)  I can create folders in the ARCHIVE folder but cannot create files !?!

It is only when I go into the /mnt/overspill directory that I can create files

is there an issue with sym links being able to be followed over to a different file system or is this a fstab issue?

any help / pointers would be greatly appreciated!

thanks
paul

---

