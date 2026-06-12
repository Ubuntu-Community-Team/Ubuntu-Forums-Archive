---
title: "How to fix &quot;exportfs: duplicated export entries&quot;?"
date: 2009-09-09
forum: General Help
---

### Post by Raymond Day on 2009-09-09
For hours I have been looking on google and can not find a fix.

I have 2 slimRIO's that I need to setup a exportfs for. I got it working.

But I like to fix this:

```
root@small:/# /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...
exportfs: duplicated export entries:
exportfs:       *:/home/part2/mystuff/slimrio/tftpboot/192.168.2.125
exportfs:       *:/home/part2/mystuff/slimrio/tftpboot/192.168.2.125
exportfs: duplicated export entries:
exportfs:       *:/home/part2/mystuff/slimrio/tftpboot/192.168.2.169
exportfs:       *:/home/part2/mystuff/slimrio/tftpboot/192.168.2.169
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
root@small:/#
```

Some how it shows duplicated export entries. I do not know how to fix this. Any one know?

But my slimRIO's are both working any way. But I like to fix this duplicated error.

-Raymond Day

---

### Post by Raymond Day on 2009-09-11
after more then a day and a reboot I get this Warning now:

```
root@small:~# /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ]
 * Exporting directories for NFS kernel daemon...
exportfs: Warning: tftpboot/192.168.2.125 does not exist
exportfs: Warning: tftpboot/192.168.2.169 does not exist
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
root@small:~#
```

It still works. But it be nice to fix this exportfs Warning. tftpboot is right at:

> drwxr-xr-x   2 root   root     112 2009-09-09 16:32 tftpboot

Inside that have:

> root@small:/tftpboot# pwd
/tftpboot
root@small:/tftpboot# ls -l
total 0
lrwxrwxrwx 1 root root 50 2008-01-03 18:19 192.168.2.125 -> /home/part2/mystuff/slimrio/tftpboot/192.168.2.125
lrwxrwxrwx 1 root root 50 2009-09-09 16:32 192.168.2.169 -> /home/part2/mystuff/slimrio/tftpboot/192.168.2.169
root@small:/tftpboot#

So I don't get why it's saying "Warning: tftpboot/192.168.2.169 does not exist"?

-Raymond Day

---

### Post by Raymond Day on 2009-09-12
I found the error.

my /etc/exports file had the link in it 2 times. So it looked like this:

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/part2/mystuff/slimrio/tftpboot/192.168.2.125 *(ro,sync,subtree_check,insecure,no_root_squash)
/home/part2/mystuff/slimrio/tftpboot/192.168.2.169 *(ro,sync,subtree_check,insecure,no_root_squash)
tftpboot/192.168.2.125 *(ro,sync,subtree_check,insecure,no_root_squash)
tftpboot/192.168.2.169 *(ro,sync,subtree_check,insecure,no_root_squash)
```

The last 2 lines are the same as the 2 lines before it. Now my /etc/exports file looks like this:

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/part2/mystuff/slimrio/tftpboot/192.168.2.125 *(ro,sync,subtree_check,insecure,no_root_squash)
/home/part2/mystuff/slimrio/tftpboot/192.168.2.169 *(ro,sync,subtree_check,insecure,no_root_squash)
```

Then I did this and get not error.

```
root@small:~# /etc/init.d/ntp restart
 * Stopping NTP server ntpd                                              [ OK ]
 * Starting NTP server ntpd                                              [ OK ]
root@small:~#
```

-Raymond Day

---

