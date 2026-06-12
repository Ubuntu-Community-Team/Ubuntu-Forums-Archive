---
title: "What is the point of permissions/ownerships on symbolic links?"
date: 2010-05-02
forum: General Help
---

### Post by abcuser on 2010-05-02
Hi,
I am trying to understand the point of permissions and ownerships on symbolic links on Ubuntu 10.04.

Sample:
I have created file FileA with user user1 which belongs to group user1:
```
touch FileA
```

Then I have created symbolic link with user root:
```
sudo ln -s FileA FileB
```

The output of "ls -l" command:
```

-rw-r--r-- 1 user1 user1  0 2010-05-02 14:23 FileA
lrwxrwxrwx 1 root root 84 2010-05-02 14:23 FileB -> FileA

```

Because there is read/write/execute to user, group and others anyone can do read/write/execute on FileB. I see I can't change permissions/ownership of symbolic link B, like "sudo chmod o-r FileB" or change ownership "sudo chown user1:user1 FileB". What is the point of having symbolic link different permissions/ownership then original FileA? Why doesn't permissions/ownership of FileB get changed when permissions/ownership of FileA gets changed (just like on hard links)?

Thanks

---

### Post by rnerwein on 2010-05-02
hi
the point is that this are not the permissions of the "lets say" the file - the contens of that file is the path to the original file.
hope this helps a little.
if you address the link you will alway address the real file and those permissions are used.
ciao

---

