---
title: "CIFS mount: unable to write with other users than root"
date: 2010-08-08
forum: General Help
---

### Post by tubededentifrice on 2010-08-08
Hi everybody,

I've set up my own movie box (Ubuntu 10.04 server x64 + XBMC) following the guide [http://wiki.xbmc.org/index.php?title=XBMCbuntu](http://wiki.xbmc.org/index.php?title=XBMCbuntu)
My movies are stored on my own Netgear ReadyNAS (NV+), mounted to XBMC through the sources.xml file:
```
<source>
     <name># Movies</name>
     <path pathversion="1">smb://xbox:XXXXXXX@192.168.1.202/Movies/</path>
</source>
```Everything is working like a charm, except I can't delete files from the XBMC interface exactly as if the mount was read-only.

To debug this, I created a mount on the system (via /etc/fstab):
```
//192.168.1.202/Movies /mnt/Movies                    cifs    defaults,username=xbox,password=XXXXXXX 0 0
```This mount is working perfectly when I'm root:
```
root@XBMC:/mnt/Movies# echo "test root" > test.root.txt
root@XBMC:/mnt/Movies# cat test.root.txt
test root
```But when I go "xbmc" (which is also the user who runs XBMC):
```
xbmc@XBMC:/mnt/Movies$ echo "test xbmc" > test.xbmc.txt
[COLOR=Red]**bash: test.xbmc.txt: Permission denied**[/COLOR]
```Of course, /mnt/Movies is chmoded to 777:
```
root@XBMC:/mnt# ls -la
total 8
drwxr-xr-x  3 root root 4096 2010-07-25 17:30 .
drwxr-xr-x 21 root root 4096 2010-08-08 16:24 ..
drwxr-xr-x  1 root root    0 2010-08-08 17:22 Movies
root@XBMC:/mnt# umount /mnt/Movies
root@XBMC:/mnt# ls -la
total 12
drwxr-xr-x  3 root root 4096 2010-07-25 17:30 .
drwxr-xr-x 21 root root 4096 2010-08-08 16:24 ..
drwxrwxrwx  2 root root 4096 2010-07-27 18:32 Movies
```I think the 2 problems are closely related, but can't understand why this is happening.

I can't figure out if the problem is due to the NAS or due to some missing permissions on the box. Could you please help me solving this issue, allowing everybody to write the share? I suspect maybe some missing options in the fstab? But if so, how to pass the mount options to XBMC?


THANKS!

---

### Post by rubylaser on 2010-08-08
The permissions on your files in your SAMBA share are showing you your problem.  They are owned by the user root and the group root, and I'm guessing you didn't recursively apply permissions to the subfolders.  To have this work properly, you should just do these two things.

```
sudo chown -R xbmc:xbmc /mnt/Movies
```

And, then set your permissions back to 775 at a minimum, if not 755.
```
sudo chmod -R 755 /mnt/Movies
```

That should get you working just fine.

---

### Post by tubededentifrice on 2010-08-09
Hello,

Unfortunately, this didn't did the trick :( I still can't write the share (exact same permission problem).

```
xbmc@XBMC:/mnt/Movies$ ls -la
total 8196
drwxr-xr-x 1 1011 libuuid     0 2010-08-08 17:22 .
drwxr-xr-x 3 root root     4096 2010-07-25 17:30 ..
drwxr-xr-x 1 1011 libuuid     0 2010-04-04 22:48 Movies
drwxr-xr-x 1 1011 libuuid     0 2010-08-08 17:51 Incoming
xbmc@XBMC:/mnt/Movies$ echo "test xbmc" > test.xbmc.txt
-su: test.xbmc.txt: Permission denied
xbmc@XBMC:/mnt/Movies$
```


(I think wrong owner is reported because users on the NAS and users on the box are not sync, but permissions should do the trick, right?)

---

### Post by rubylaser on 2010-08-09
Your owner is still wrong on your Movies share.  This line shows you that...
```
drwxr-xr-x 1 [COLOR="Red"]1011[/COLOR] [COLOR="red"]libuuid[/COLOR]     0 2010-04-04 22:48 Movies
```
This is showing that it's owner by user 1011, and group libuuid, it should look like this...
```
drwxr-xr-x 1 **xbmc** **xbmc**     0 2010-04-04 22:48 Movies
```

I'm guessing that you don't have an xbmc user created on your NAS and that's why you got weird results. Try this on the NAS, or create a user on the device with whatever mechanism it supports.

```
sudo adduser xbmc
```

Give that user a password, and then chown the directory again.
```
sudo chown -R xbmc:xbmc /mnt/Movies
```

---

