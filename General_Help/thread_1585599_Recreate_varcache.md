---
title: "Recreate /var/cache?"
date: 2010-09-30
forum: General Help
---

### Post by Glaucous on 2010-09-30
I wanted to put /var/cache on tmpfs/RAM, and deleted the /var/cache and mounted. But apparently apt-get wants these folders at all times, and can't recreate them (/var/cache/archives for instance), and I have to do it manually.

Now, is there a way to do this automatically?

---

### Post by CharlesA on 2010-09-30
So you need to have it create them after each boot?

Question: Why do you want the package cache in RAM? It doesn't take up all that much space on the hard drive in the first place.

---

### Post by Glaucous on 2010-09-30
No I just need to recreate them once (won't be using tmpfs).
I wanted the .deb files on RAM to "help" the SSD, I rarely need the .debs twice.

I'm thinking that I could just copy from another Ubuntu /var, or just the Live CD, wouldn't be any problem doing that I guess?

---

### Post by CharlesA on 2010-09-30
I see.

Here are how the permissions are set for each folder:
```
charles@atlantis:~$ ls -ld /var
drwxr-xr-x 14 root root 4096 2010-09-23 17:41 /var
charles@atlantis:~$ ls -ld /var/cache/
drwxr-xr-x 7 root root 4096 2010-09-23 17:41 /var/cache/
charles@atlantis:~$ ls -ld /var/cache/apt/
drwxr-xr-x 3 root root 4096 2010-09-30 06:41 /var/cache/apt/
charles@atlantis:~$ ls -ld /var/cache/apt/archives/
drwxr-xr-x 3 root root 36864 2010-09-27 14:06 /var/cache/apt/archives/

```

You should be able to just recreate the directories and be ok. You could even copy the cache from another install, and it would probably work ok.

There is also a file called "lock" in there:
```
-rw-r----- 1 root    root           0 2010-09-23 17:37 lock
```

As well as a directory called "partial":

```
drwxr-xr-x 2 root    root        4096 2010-09-27 14:06 partial
```

---

### Post by Glaucous on 2010-09-30
Okay everything seems to be working, took a look at my laptop and checked the /var/cache/man which seemed to be annoyed as well.

Thanks for your help. Still think it's odd that a folder called cache can't be deleted without having to recreate.

---

