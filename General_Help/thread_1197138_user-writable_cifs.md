---
title: "user-writable cifs"
date: 2009-06-25
forum: General Help
---

### Post by uglyoldbob on 2009-06-25
I have a macintosh with a folder shared and I am having trouble mounting it under Ubuntu.

Here is the appropriate line from mount -l
//192.168.0.99/thomas on /media/test type cifs (rw,noexec,nosuid,nodev,username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777,umask=000)

Automounting works great. The only problem with this is that only root can write to it. How can I change this so that a user can write?

---

### Post by blueridgedog on 2009-06-25
Change the ownership of /media/test and add a uid argument to your mount command:

```
sudo chown USER:USER /media/test
```

(where you users name replaces USER).

Your uid is probably 1000, but you can check it with

```
cat /etc/passwd | grep USER
``` 

(again, change USER).

From 

man mount.cifs


```
      uid=arg
           sets the uid that will own all files on the mounted filesystem. It
           may be specified as either a username or a numeric uid. For mounts
           to servers which do support the CIFS Unix extensions, such as a
           properly configured Samba server, the server provides the uid, gid
           and mode so this parameter should not be specified unless the
           server and client uid and gid numbering differ. If the server and
           client are in the same domain (e.g. running winbind or nss_ldap)
           and the server supports the Unix Extensions then the uid and gid
           can be retrieved from the server (and uid and gid would not have to
           be specifed on the mount. For servers which do not support the CIFS
           Unix extensions, the default uid (and gid) returned on lookup of
           existing files will be the uid (gid) of the person who executed the
           mount (root, except when mount.cifs is configured setuid for user
           mounts) unless the "uid=" (gid) mount option is specified. For the
           uid (gid) of newly created files and directories, ie files created
           since the last mount of the server share, the expected uid (gid) is
           cached as long as the inode remains in memory on the client. Also
           note that permission checks (authorization checks) on accesses to a
           file occur at the server, but there are cases in which an
           administrator may want to restrict at the client as well. For those
           servers which do not report a uid/gid owner (such as Windows),
           permissions can also be checked at the client, and a crude form of
           client side permission checking can be enabled by specifying
           file_mode and dir_mode on the client. Note that the mount.cifs
           helper must be at version 1.10 or higher to support specifying the
           uid (or gid) in non-numeric form.

       gid=arg
           sets the gid that will own all files on the mounted filesystem. It
           may be specified as either a groupname or a numeric gid. For other
           considerations see the description of uid above.
```

The options would then be:

(rw,noexec,nosuid,nodev,username=***,password=***,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777,umask= 000)

---

### Post by uglyoldbob on 2009-06-25
Thanks, that did the trick.

---

