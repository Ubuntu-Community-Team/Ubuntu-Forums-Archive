---
title: "Set permission for files in ntfs for sharing in samba"
date: 2012-06-28
forum: General Help
---

### Post by Vishnu V on 2012-06-28
hi i would like to share a folder, which is ntfs file system.
I try to set the permission
```

sudo chmod -R o+rx /media/storage/share

```
i dont get any error, but permission is not changed

I can't acces that folder samba share

How can i set permission to folder


Please help

Thank You
Vishnu V

---

### Post by dino99 on 2012-06-28
[http://ubuntuforums.org/showthread.php?t=1586804](http://ubuntuforums.org/showthread.php?t=1586804)

---

### Post by Morbius1 on 2012-06-28
It sounds like /media/storage is either an external USB drive or an internal partition that you are mounting through Nautilus when needed. 
Both of those partitions will mount with you as owner and permissions of 700 and you can't change permissions on NTFS outside of fstab.

So I would suggest adding the following line to /etc/samba/smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to you own user name*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```[COLOR=Blue]**NOTE**[/COLOR]: Where you put that line depends on how you created the samba share:

** If you added the share in smb.conf itself then put it as part of the share definition.

** If you created the share using Nautilus then add it to the [global] section - right under the "workgroup" line is where I would put it.

---

### Post by bab1 on 2012-06-28
> **Morbius1 said:**
> ...
** If you created the share using Nautilus then add it to the [global] section - right under the "workgroup" line is where I would put it.

For usershares I believe you can add this to the [global] section ```
usershare template share
```... then create a a share like this ```
[template] 
force user = foo
```

This appears to allow you do define a template share that works as a basic template for Nautilus created shares.  I've never used it, but if it works it provides lots of possibilities for other usershare configuration.

From the man pages```
usershare template share

    Names a pre-existing share used as a template for creating 
    new usershares. All other share parameters not specified in 
    the user defined share definition are copied from this 
    named share.
```

Comments?

---

### Post by Vishnu V on 2012-06-28
Thank you very much dino99,Morbius1 and bab1
My Problem Solved :-)

---

### Post by Morbius1 on 2012-06-28
> **bab1 said:**
> For usershares I believe you can add this to the [global] section ```
usershare template share
```... then create a a share like this ```
[template] 
force user = foo
```This appears to allow you do define a template share that works as a basic template for Nautilus created shares.  I've never used it, but if it works it provides lots of possibilities for other usershare configuration.

Now that's an interesting idea. 

One could argue there's no difference to just setting a global parameter but if you use a mix of Classic shares and Usershares then you might not want a "force user" to be applied to the Classic shares depending on how you set these things up. Maybe for a multi-user system you could even replace "force user" with a "inherit owner = yes" although in this particular case I guess it wouldn't have solved the problem. Then there's the problem is the owner of the parent directory is root. Have to think about all this a bit but you're right that does open up some possibilities.

---

