---
title: "samba/cifs network hardrive mount"
date: 2010-10-01
forum: General Help
---

### Post by coolgenes on 2010-10-01
I am trying to mount a network harddrive using samba or cifs.  I have 3 users therefore 3 logins to my computer running Ubuntu 10.04.  two of them can use the same login and password to the NAS (a Synology 1010+).  The other (administrator) will use a different login and password to the NAS.  I can get a mount using:

//xxx.xxx.xxx.xxx/SharedFoldername /mnt/name cifs user,uid=osloginname,gid=users,rw,suid,credentials=/etc/cifspwd 0 0

my problem is allowing the other NAS login and password to be used by the other logins on the computer.  Does anyone know how to set up such system.  Whether I have to make another mount is no big deal as long as everyone has their own mounted harddrive upon login.

---

### Post by btindie on 2010-10-01
How about something like [AutoFS]("http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs")?

---

### Post by btindie on 2010-10-01
...or even [pam_mount]("http://packages.ubuntu.com/lucid/libpam-mount") which allows you to have user definable volume mounts.
[]("http://packages.ubuntu.com/lucid/libpam-mount") 
[http://manpages.ubuntu.com/manpages/lucid/man5/pam_mount.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/pam_mount.conf.5.html)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
 
The current version uses an XML style configuration file
```
<volume   user="user"   fstype="cifs"  server="fileserver"  path="public"
       mountpoint="/media/public" />
```

---

### Post by coolgenes on 2010-10-02
Thanks, I haven't seen those in my search so far, they look promising.  I hope one of them works and I can mark this thread solved in a couple days.

---

