---
title: "Permission denied as root"
date: 2009-08-28
forum: General Help
---

### Post by 5circles on 2009-08-28
I've never understood why I get permission denied with a sudo or sudo su when searching for files.   But now that I'm trying to recover from a stupid mistake and look exhaustively for files I think it is time to learn.

I run the following either with sudo or sudo su:

```
find / -name '*.sql'
``` 

I get 
```
find: /home/username/.gvfs: Permission denied

```

It looks like the reason is something to do with the ownership / permissions on the .gvfs directory.  ls -s as the user shows nothing out of the ordinary, but sudo ls -s shows

```
d????????? ?  ?  ?    ?   ?   .gvfs
```

I've seen the same error other times too, but never looked at the details before.

Can someone a) explain what's going on and b) tell me how to search through all files without generating errors?

Thanks
Mike

---

### Post by andrew.46 on 2009-08-28
Hi Mike,

So the *exact* syntax that fails is the following? :

```
sudo find / -name '*.sql'
```

Seems a little odd...

Andrew

---

### Post by 5circles on 2009-08-28
> **andrew.46 said:**
> Hi Mike,

So the *exact* syntax that fails is the following? :

```
sudo find / -name '*.sql'
```

Seems a little odd...

Andrew

Yes, that's the exact syntax.  Seems odd to me too:)  I've never dug into this kind of problem before.

Mike

---

### Post by uylug on 2009-08-28
.gvfs is a private directory **only** the original owner can read. I think it is encrypted or something, and it is used to mount remote locations such as ftp folders and stuff like that.

---

### Post by blueridgedog on 2009-08-28
See this thread:

[http://ubuntuforums.org/showthread.php?t=791693](http://ubuntuforums.org/showthread.php?t=791693)

Post 6

---

### Post by amac777 on 2009-08-28
.gvfs is a special mount point that can only be read by the user that created it so root can't read it. From Fred's post on: [https://answers.launchpad.net/ubuntu/+question/34333](https://answers.launchpad.net/ubuntu/+question/34333)

> Hi,

.gfvs is a FUSE mount point :
$ mount|grep gvfs
gvfs-fuse-daemon on /home/fred/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fred)

This mount is setup so that only the user logged in can view it.

The fact that root cannot this directory seems to be a FUSE limitation. See :
[http://bugzilla.gnome.org/show_bug.cgi?id=534284](http://bugzilla.gnome.org/show_bug.cgi?id=534284)
and :
[https://bugs.launchpad.net/gvfs/+bug/225361](https://bugs.launchpad.net/gvfs/+bug/225361)

Hope it helps.

---

### Post by uylug on 2009-08-28
So it was a bug uh. Lol. Thought it was some kind of encryption haha.

---

### Post by ad_267 on 2009-08-28
That error doesn't matter anyways. When you run find it will give you an error for that directory, but it will still search all of the other directories.

---

### Post by 5circles on 2009-08-28
Thanks everyone.  I guess I understand (a bit) and will read up more about fuse.  Now back to the recovery from my stupid mistake.

--Mike

---

### Post by gabak on 2009-08-28
use locate instead it is better
sudo -i
updatedb
locate filename.exe


> **5circles said:**
> I've never understood why I get permission denied with a sudo or sudo su when searching for files.   But now that I'm trying to recover from a stupid mistake and look exhaustively for files I think it is time to learn.

I run the following either with sudo or sudo su:

```
find / -name '*.sql'
``` 

I get 
```
find: /home/username/.gvfs: Permission denied

```

It looks like the reason is something to do with the ownership / permissions on the .gvfs directory.  ls -s as the user shows nothing out of the ordinary, but sudo ls -s shows

```
d????????? ?  ?  ?    ?   ?   .gvfs
```

I've seen the same error other times too, but never looked at the details before.

Can someone a) explain what's going on and b) tell me how to search through all files without generating errors?

Thanks
Mike

---

### Post by ad_267 on 2009-08-28
> **gabak said:**
> use locate instead it is better
sudo -i
updatedb
locate filename.exe

Different tools for different jobs. Find is very powerful due to its ability to do lots of stuff with the files once you find them and search within a given directory. Locate is good for finding a file very quickly anywhere within the file system.

---

