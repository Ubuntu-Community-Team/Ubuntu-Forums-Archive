---
title: "subversion server webdav cannot open svn filesystem"
date: 2010-05-02
forum: General Help
---

### Post by rmills on 2010-05-02
First, I followed the instruction here: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion).

I'm getting an error when I try to access my subversion repository via WebDAV.  I'm able to browse, checkout, commit, etc if I access it via the "file://" prefix.  Trying to browse it with the svn command or in a browser using "http://" gives me an error:
```
<D:error>
<C:error/>
<m:human-readable errcode="13">
Could not open the requested SVN filesystem
</m:human-readable>
</D:error>
``` 

Looking in the apache logs I can see where it's failing:
```
[Sun May 02 21:12:02 2010] [error] [client 192.168.1.126] (20014)Internal error: Can't open file '/home/shares/svn/repos/myproject/format': Permission denied
[Sun May 02 21:12:02 2010] [error] [client 192.168.1.126] Could not fetch resource information.  [500, #0]
[Sun May 02 21:12:02 2010] [error] [client 192.168.1.126] Could not open the requested SVN filesystem  [500, #13]
[Sun May 02 21:12:02 2010] [error] [client 192.168.1.126] Could not open the requested SVN filesystem  [500, #13]

```

So I double checked the permissions on my repository, and everything looks ok to me:
```
$ ls -la /home/shares/svn/repos/myproject/
total 32
drwxrwsr-x 6 www-data subversion 4096 2010-04-30 11:46 .
drwxr-xr-x 3 www-data shares     4096 2010-04-30 11:40 ..
drwxrwsr-x 2 www-data subversion 4096 2010-04-30 11:46 conf
drwxrwsr-x 6 www-data subversion 4096 2010-04-30 11:46 db
-r--rwSr-- 1 www-data subversion    2 2010-04-30 11:46 format
drwxrwsr-x 2 www-data subversion 4096 2010-04-30 11:46 hooks
drwxrwsr-x 2 www-data subversion 4096 2010-04-30 11:46 locks
-rw-rwSr-- 1 www-data subversion  229 2010-04-30 11:46 README.txt
```

In the interest of full disclosure, user www-data and me (only user on the server so far) are in the "subversion" and "shares" groups.  And here's my dav_svn.conf:
```
<Location /svn/myproject>
        DAV svn
        SVNPath /home/shares/svn/repos/myproject
</Location
```

TIA :confused:

---

### Post by rmills on 2010-05-04
bump

---

