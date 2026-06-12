---
title: "mount and fstab setting uid,gid"
date: 2011-12-31
forum: General Help
---

### Post by linuxcss on 2011-12-31
sudo mount -t vboxsf shared mnt -o uid=1000,gid=1000

what is the equivalent entry needed in fstab to mount at boot time
for the above mount command?

---

### Post by WorMzy on 2011-12-31
```
[COLOR="Red"]<identifier>[/COLOR] /mnt vboxsf auto,uid=1000,gid=1000 0 0
```

I'm not sure what "shared" is in your mount statement, and I'm assuming that "mnt" means /mnt. You'll need to put in the identifier* yourself.



*without the '<>'

---

### Post by Morbius1 on 2011-12-31
I don't know what version of VBox you are using but beginning with V4 it mounts the shared folders automaticlly for you all by itself.

The shares are mounted at: /media/sf_share-name
[COLOR=Blue]* The "sf-" indicates it is the VBox "shared folder"*[/COLOR]

What Xubuntu may not do however is make you a member of the  shared folder group by default so you need to add yourself:
```
sudo gpasswd -a morbius vboxsf
```Then logoff and logon again. You should now have read / write access to the shared folder in /media.

---

### Post by linuxcss on 2011-12-31
thanks 
that worked

---

