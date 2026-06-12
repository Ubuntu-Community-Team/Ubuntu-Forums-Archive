---
title: "Crazy /usr/ full issues"
date: 2012-02-16
forum: General Help
---

### Post by ntaforge on 2012-02-16
Hey everybody

Sorry if this has been posted before. I try to search everywhere before posting!

So I have this issue where my /usr/ partition has been claimed to be full. I have 50G set aside for it!

When I run 

```
sudo du -csh /*
```


```

7.9M	/bin
30M	/boot
976K	/dev
30M	/etc
du: cannot access `/home/*myname*/.gvfs': Permission denied
111G	/home
0	/initrd.img
203M	/lib
12M	/lib32
0	/lib64
16K	/lost+found
4.0K	/media
4.0K	/mnt
109M	/opt
du: cannot access `/proc/2839/task/2839/fd/4': No such file or directory
du: cannot access `/proc/2839/task/2839/fdinfo/4': No such file or directory
du: cannot access `/proc/2839/fd/4': No such file or directory
du: cannot access `/proc/2839/fdinfo/4': No such file or directory
0	/proc
176K	/root
13M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
84K	/tmp
**46G	/usr**
1.1G	/var
0	/vmlinuz
158G	total

```


Which that 46G  cannot be true!

So then I ran 

```

sudo du -csh /usr/*

```

```

224M	/usr/bin
36K	/usr/games
18M	/usr/include
1.7G	/usr/lib
340M	/usr/lib32
0	/usr/lib64
140K	/usr/local
16K	/usr/lost+found
33M	/usr/sbin
1.5G	/usr/share
105M	/usr/src
**3.8G	total**

```



Has anyone ever seen this?

Please help!
Thanks

---

### Post by 1clue on 2012-02-16
Do you have any invisible files in your /usr directory?

**ls -alh /usr**

---

### Post by ntaforge on 2012-02-16
Right so somehow most of my home directory was copied into a hidden folder.

Don't know about that but ok!

Thanks for your help 1clue!

---

### Post by 1clue on 2012-02-16
Did you use lvm2 on your installation?

If you're going to use multiple partitions it makes sense to make them easily resizable.

I don't know how Ubuntu currently does it because I haven't let any distro handle my formatting for years.

---

### Post by dcstar on 2012-02-16
> **ntaforge said:**
> Hey everybody

Sorry if this has been posted before. I try to search everywhere before posting!

So I have this issue where my /usr/ partition has been claimed to be full. I have 50G set aside for it!
...........

The /usr folder is a **System Folder** that **you** should not ever be touching. There is no need for it to be anywhere near 50GB in a normal system.

---

