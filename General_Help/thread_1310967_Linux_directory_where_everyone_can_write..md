---
title: "Linux directory where everyone can write."
date: 2009-11-02
forum: General Help
---

### Post by Zeemvel on 2009-11-02
Hi,

Is there a standard directory in linux distributions where all users can write to?

/home/username isn't good because that is per-user.
/etc/ isn't good because apparantly only a superuser can write to it
/tmp/ isn't good because it's temporary

I'm making an application where I want to store settings that can be read and written by all users, hence the need for a directory that everyone can touch. I thought /etc/ would be it but now I discovered I can't make a subdir in it without being superuser...

---

### Post by hal10000 on 2009-11-02
/etc is no good idea. None of the existing directories is a good idea.

But you can create a new directory and make it writeanle for everyone:
```
sudo mkdir /shared_dir
sudo chmod a+w /shared_dir

```

With the first command you create a new directory called shared_dir directly under the root ( / ) directory.
The second command makes it writeable for everyone. But alsoeveryone can delete a file, no matter if he/she created it by himself.

If you want to avoid this and only allow users to delete files which they created theirselves, then perform
```
sudo chmod +t /shared_dir
```

If you want to know more about the linux file hierarchy read this: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

