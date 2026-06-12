---
title: "unable to SMB mount as regular user"
date: 2010-08-10
forum: General Help
---

### Post by andimeier on 2010-08-10
Hi forum!

seems like I'm missing something: I want to mount a SMB share as a regular user (on Ubuntu Lucid).

I checked that:
(1) /etc/fstab contains an entry for the mount with the option "user"
(2) the mount directory is owned by the user who should be able to mount the SMB share

What else?

I would like to mount the SMB share //ams150/readonly onto the directory /mnt/ams150, using the user andi (let the password be: secretpwd)

So, my /etc/fstab contains the following entry:

//ams150/readonly       /mnt/ams150     smbfs    user,nosuid,noauto,user=andi,password=secretpwd 0 0


Next, a "ls -l" shows that the user andi actually owns the mountpoint (which good, I suppose):

andi@lucid:/mnt> ls -l
drwxrwxrwx 2 andi andi 4096 2010-08-08 18:56 ams150

Now, when I try to mount as user andi, the following happens:

andi@lucid:/mnt> mount /mnt/ams150
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

What's wrong? 

Thanx for all hints!
Andi

---

### Post by endotherm on 2010-08-10
I've always had to use sudo with smbmount, even when the mountpoint is within my home. I think especially mounting to /mnt you will need root.

---

### Post by mathgeek2000 on 2010-11-19
According to what I've read, -- also trying to solve this bug/feature --
At least under 10.04.1 Lucid, the following works:

As regular user:

```
## Set sticky bit on mount.cifs
$sudo chmod +s `which mount.cifs` ### <- that's as a super user
$ smbmount //server/share /<Your Directory> -o username=<smb user>,password=<smb password

```

You need write permission on the mount directory, but you also need the sticky bit set on the above command. According to this site:
  [http://chris.brookins.info/2010/04/29/smbmount-mount-error1/](http://chris.brookins.info/2010/04/29/smbmount-mount-error1/)
setting the sticky bit on smbmount instead worked on 10.04 (the earlier Lucid)
but the above fix didn't work on 10.10

Though it may be chris didn't have write access to the mount directory. 
  -- that seems to be a safety feature of Ubuntu.

---

