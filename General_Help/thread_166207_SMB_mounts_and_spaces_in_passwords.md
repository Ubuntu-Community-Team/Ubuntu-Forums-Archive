---
title: "SMB mounts and spaces in passwords"
date: 2006-04-26
forum: General Help
---

### Post by cracker on 2006-04-26
Hello, I'm trying to set my fstab to mount samba shares with a space in the password. Here is an example of it:

//computer/f   /mnt/computer/f   smbfs  noauto,user=user,password="my password"    0 0

It works using the mount command manually, like this:

$ mount /mnt/computer/f -o user=user,password="my password"

However, I have no way of escaping the space in fstab and still having it work. Quotes as used don't work, neither do single quotes. By reading the man page, I tried using \040 to escape a space, as in the share name, but it fails with incorrect login details. Any way around this?

---

### Post by kzutter on 2006-04-26
I cannot test it here, but I wonder if it would work if you used a credentials file.
Try both the quoted and unquoted password in the credentials file.

here is my fstab line using credentials:
//mars/Ken /mnt/mars/Ken smbfs rw,credentials=/etc/samba/credentials  0 0

and here is my credentials file (/etc/samba/credentials):
username=ken
password=fooberry

---

### Post by gerbman on 2006-04-26
[QUOTE=kzutter]I cannot test it here, but I wonder if it would work if you used a credentials file.
Try both the quoted and unquoted password in the credentials file.

here is my fstab line using credentials:
//mars/Ken /mnt/mars/Ken smbfs rw,credentials=/etc/samba/credentials  0 0

and here is my credentials file (/etc/samba/credentials):
username=ken
password=fooberry[/QUOTE]If you do use a credentials file, make sure to set the permissions appropriately. Do something like```
chmod 600 /path/to/credentials/file
```

---

### Post by cracker on 2006-04-26
EDIT: That works great. I forgot the one machine wasn't set up to share yet. :S  Thanks for all the help.

---

### Post by cracker on 2006-04-26
Ok, now I'm having a new problem...
I have three computers I am trying to access. One is running XP Home, one is running XP Pro SP1, and the other is running 2000 Pro SP4. All these machines have my user (ryan) as an administrator with the same password. However, only the one running XP Home will allow me to mount the share. All the shares work through other windows machines, so I'm guessing it has to do with some kind of encryption or security...Anyone have some ideas?

---

