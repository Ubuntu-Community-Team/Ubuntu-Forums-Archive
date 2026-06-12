---
title: "Permenantly &amp; Securly mount Windows folder share"
date: 2011-09-16
forum: General Help
---

### Post by slydogsz on 2011-09-16
Running Ubuntu 11.04 desktop how do I securely and permanently mount shares from a windows 2008 R2 server so that I can read and write to them and dont have to remap them every reboot. I do not want to store my domain credentials in a plain text file and I dont want to join the linux system to the AD.

Is this possible to do and if so how ?

Thanks in advance.

---

### Post by michaelb28 on 2011-09-16
I don't know how to store your credentials in a non-plaintext file.  But...

Some people put their credentials in a file that only the root user can access and modify their /etc/fstab file to mount the windows share using this file.  The password is still plaintext, but only to those with root access. However, this approach no longer works with versions of smbfs since 2009 according to this page:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

If you only need it mounted when you login, and your ubuntu username and password are the same as on the windows machine, you might consider using libpam_mount

See towards the end of this page:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by slydogsz on 2011-09-16
I have seen this article but it does not look up to date. I am using 11.04 it is for 9.04 and is a work in progress that hasn't been updated at a guess since 2009.

---

### Post by michaelb28 on 2011-09-17
You might try gvfs-mount. It should store the password in the gnome-keyring.

[http://www.techytalk.info/mount-remote-share-at-login-ubuntu-linux-using-gvfs-mount/](http://www.techytalk.info/mount-remote-share-at-login-ubuntu-linux-using-gvfs-mount/)

---

