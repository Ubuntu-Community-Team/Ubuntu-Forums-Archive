---
title: "CIFS mount only root can do that"
date: 2009-08-18
forum: General Help
---

### Post by PomCompot on 2009-08-18
Hi,

I encounter a problem mounting a Samba NAS share at my office.

I want to be able to mount this share as user because I'm on a laptop and don't want this share to be automount when I'm at home for instance.

I have already search a lot on the web, this forums and other Linux forums but couldn't find a solution.

I have set /sbin/mount.cifs SUID like this command show it:
```
$ls -l /sbin/mount.cifs
-rwsr-xr-x 1 root root 30704 2009-07-08 09:28 /sbin/mount.cifs
```

I have put this line in my /etc/fstab:
```
//<hostname>/<share>	/media/mountpoint	cifs	users,suid,domain=<domain_name>,credentials=/etc/samba/credentials,iocharset=utf8,uid=1000,gid=1000,noauto	0	0
```

I have the following rights on the mount point:```

$ls -l /media/
drwxr-xr-x  2 stephane stephane  4096 2009-07-20 15:31 mountpoint
```

My uid:
```
$id
uid=1000(stephane) gid=1000(stephane) groupes=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(stephane)
```

I achieve to mount the share as a user with this command in the terminal:
```
$mount.cifs //<hostname>/<share>	/media/mountpoint -o sers,suid,domain=<domain_name>,credentials=/etc/samba/credentials,iocharset=utf8,uid=1000,gid=1000,noauto
```

But, those following commands don't work:
```
$mount /media/mountpoint
mount: only ROOT can do that
```
or
```
$mount -t cifs //<hostname>/<share>	/media/mountpoint -o sers,suid,domain=<domain_name>,credentials=/etc/samba/credentials,iocharset=utf8,uid=1000,gid=1000,noauto
mount: only ROOT can do that
```

Logically, this command also succeed, but i's not what I want:
```
$sudo mount /media/mountpoint
```

I don't understand why it's work when invoking directly mount.cifs and not with mount.

Thanks in advance for your help.

---

### Post by slakkie on 2009-08-18
I would help you, but I'm not at work atm, where I have samba running as well.. At home I'm samba less..

---

### Post by slakkie on 2009-08-20
I have the followinf fstab entries:

```

\\19X.1XX.X.XX\data$ /mnt/samba/office-server/XXXX  cifs user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb-xxxxx,workgroup=xxxxx,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

```

When I try to mount it

```

wesleys@eniac:/home/wesleys$ mount /mnt/samba/office-server/XXXX 
/mnt/samba/office-server/wndsrv002
mount error: permission denied or not superuser and mount.cifs not installed SUID

```

If you download the source of the smbfs package you will see changelog entries where Debian actually reverted the SUID of (u)mount.cifs. Don't know why this is the case.

After some digging I found:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/106146](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/106146)

I'm unable to find what arguments I should add to the rules file to enable suid on (u)mount.cifs. Most likely it will be ./configure --enable-setuid, so add the --enable-setuid to the rules file and recreate the .deb file and install it.

Maybe file a new bug report, ask for a package with suid and one without, so users can decide what they want?

---

### Post by PomCompot on 2009-08-21
Yes. I have already got this message and solved it with:
```
sudo chmod u+x /sbin/mount.cifs
```

As you can see with my example commands, I can use mount.cifs as user when directly invoking it. So I don't think the problem relies on this.

The problem is now another one. But how to solve it? Mystery.

---

### Post by PomCompot on 2009-08-21
GOT IT!

Ok, the solution is not trivial. It's a mix of user permissions and sticky bits on the rights things.

First, the /etc/fstab line keeps unchanged:
```
//<hostname>/<share>	/media/mountpoint	cifs	users,suid,domain=<domain_name>,credentials=/etc/samba/credentials,iocharset=utf8,uid=1000,gid=1000,noauto	0	0
```

Next, the mount point permissions, it must be owned by the user declared in the fstab line (nothing to change for me):
```
$ls -l /media/
drwxr-xr-x  2 stephane stephane  4096 2009-07-20 15:31 mountpoint
```

Next, the SUID bit on mount.cifs must be set:
```
sudo chmod u+s /sbin/mount.cifs
```

Idem on /sbin/umount.cifs.

Next, the SUID bit on mount MUST NOT BE SET!
```
sudo chmod u-s /bin/mount
```

This must NOT be done on /bin/umount.

No more message only root can do that with this.

Question now: What is the default mount permissions? Does somebody could send here the result of:
```
ls -l /bin/mount
```

I don't know if there is side effects to this. I anyone could bring a light on this. Will see it in the long term either.

---

### Post by slakkie on 2009-08-21
That is tricky, if different users want to mount the CIFS filesystem then you need to keep chowning the mountpoint. Maybe set some correct group permissions on that dir.

---

### Post by PomCompot on 2009-08-21
I have tried this with:
```
sudo chown root:plugdev /media/mountpoint
```
and user + group SUID on mount.cifs
```
sudo chmod +s /sbin/mount.cifs
```
and this in /etc/fstab
```
[…] uid=1000,gid=46 […]
```

But that don't work. I get:
```
mount /media/mountpoint
mount error: permission denied or not superuser and mount.cifs not installed SUID
```

Moreover, I still get a problem with my previous solution because I get this message when trying to umount:
```
umount /media/mountpoint
umount: /media/mountpoint isn't mounted according to mtab (<- translated from French, don't know if exact English terms)

```

I have to do a lazy root unmount:
```
sudo umount -l /media/mountpoint
```

Strange. It's why I'm interested in your /bin/mount and /bin/umount permissions.

---

