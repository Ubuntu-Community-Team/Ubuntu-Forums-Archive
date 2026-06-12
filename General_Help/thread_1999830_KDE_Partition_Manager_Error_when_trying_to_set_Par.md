---
title: "KDE Partition Manager Error when trying to set Partition Label"
date: 2012-06-08
forum: General Help
---

### Post by Jack Nitro on 2012-06-08
I know someone's going to run in and tell me to use gparted, but I need to use a partition editor with ntfs support, which gparted doesn't have (at least the last time I checked).

[[img]http://s15.postimage.org/jd1071em2/Screenshot_at_2012_06_08_16_07_20.jpg[/img]](http://s15.postimage.org/ftf2h8bw9/Screenshot_at_2012_06_08_16_07_20.png)

Everything else works fine, and it seems to make the ntfs filesystem without any issue, but it coughs up when it tries to set the system label, which makes everything fail. Help?

---

### Post by PhantomTurtle on 2012-06-08
I just tried gparted and it seems to be able to format in NTFS(version 0.11 on precise). If you cannot though, I read that NTFS support can be enabled (If for some reason it isn't for you) (As shown in this article - [http://hydtech.wordpress.com/2009/05/24/how-to-enable-hfs-support-in-gparted/]("http://hydtech.wordpress.com/2009/05/24/how-to-enable-hfs-support-in-gparted/")). To try to format with NTFS, install gparted and then run this command in terminal,
```
sudo apt-get install hfsplus hfsutils hfsprogs ntfsprogs
```

---

### Post by Jack Nitro on 2012-06-09
Well, that's convenient. Thanks for the info, it was able to work in gparted without issue.

It is kind of annoying, though, that ntfsprogs uninstalls ntfs-3g, which I kinda need.

---

### Post by PhantomTurtle on 2012-06-10
> **Jack Nitro said:**
> Well, that's convenient. Thanks for the info, it was able to work in gparted without issue.

It is kind of annoying, though, that ntfsprogs uninstalls ntfs-3g, which I kinda need.

I'm guessing you need ntfs-3g to mount that partition. There is no way to have them both installed since ntfsprogs was superseded by ntfs-3g. I guess when you are done partitioning you can reinstall ntfs-3g and remove ntfsprogs(which is no longer needed unless you want format another partition or reformat that one).

---

