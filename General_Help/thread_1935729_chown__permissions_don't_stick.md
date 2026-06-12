---
title: "chown / permissions don't stick"
date: 2012-03-04
forum: General Help
---

### Post by Tehut on 2012-03-04
So, permissions for a folder got ****** up and I need to fix them. I tried to do
sudo chmod ugo+rwx [folder]
sudo chown root [folder]
sudo chgrp root [folder]
but, the changes don't stick. The files are still marked as non-executable and the owner is still my normal user. The files are on ext4, so there should not be any problems with permissions like on NTFS. I'm not getting any errors either, just nothing happens.
If anyone has any idea what might cause this/how to fix it, thank you very much.

---

### Post by Khayyam on 2012-03-05
> **Tehut said:**
> I tried to do:

```
sudo chmod ugo+rwx [folder]
sudo chown root [folder]
sudo chgrp root [folder]
```

but, the changes don't stick. The files are still marked as non-executable and the owner is still my normal user. The files are on ext4, so there should not be any problems with permissions like on NTFS. I'm not getting any errors either, just nothing happens.

You are only telling chmod to change permissions on the directory and not the content of that directory.

```
% mkdir -p test/test{1,2,3}
% ls -ld test/*
drwxr-xr-x  2 user  group  68  5 Mar 06:01 test/test1/
drwxr-xr-x  2 user  group  68  5 Mar 06:01 test/test2/
drwxr-xr-x  2 user  group  68  5 Mar 06:01 test/test3/
% sudo chown -R root:wheel test
% ls -ld test/*
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test1/
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test2/
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test3/
% sudo chmod -R g-rx test/
% ls -ld test/*
drwx---r-x  2 root  wheel  68  5 Mar 06:01 test/test1/
drwx---r-x  2 root  wheel  68  5 Mar 06:01 test/test2/
drwx---r-x  2 root  wheel  68  5 Mar 06:01 test/test3/
% sudo chmod -R g+rx test/
% ls -ld test/*
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test1/
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test2/
drwxr-xr-x  2 root  wheel  68  5 Mar 06:01 test/test3/
% sudo chmod -R ugo+rwx test
% ls -ld test/*
drwxrwxrwx  2 root  wheel  68  5 Mar 06:01 test/test1/
drwxrwxrwx  2 root  wheel  68  5 Mar 06:01 test/test2/
drwxrwxrwx  2 root  wheel  68  5 Mar 06:01 test/test3/
% whoami
user
% [COLOR=DarkRed]rm -fr test[/COLOR]
% ls -ld test/*
ls: test/*: No such file or directory
```

So, it should be clear that '-R' is recursive. It should also make clear the danger of setting permissions to 'ugo+rwx' ... that means anyone can read, and write, and so 'rm -fr'. User, group and other need rx to read the directory but not +w. Similarly with files so u+rwx g+rx.

Also, dependent on whats in the directory some files (pdf's, mp4's) doen't need the executable flag set so -R should be used with some understanding of what the directory contains.

HTH ... khay

---

### Post by Tehut on 2012-03-05
Thank you very much, that did the trick.
Yeah, I'm aware of the possible dangers. Not a problem in this case.

---

### Post by Khayyam on 2012-03-05
> **Tehut said:**
> Thank you very much, that did the trick.Yeah, I'm aware of the possible dangers. Not a problem in this case.

Your welcome ... but there are no files, or directories, that need to be ugo+rwx, danger or not.

Anyhow ... you can now [mark the thread as [SOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

best ... khay

---

### Post by PCFreak2 on 2012-03-05
Tip:
I prefer numbers in chmod

Example:

```
chmod 755 file.txt
```

---

