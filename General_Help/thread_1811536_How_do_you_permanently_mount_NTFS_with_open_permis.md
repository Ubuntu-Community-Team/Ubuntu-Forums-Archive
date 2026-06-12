---
title: "How do you permanently mount NTFS with open permissions so that I can use SAMBA?"
date: 2011-07-25
forum: General Help
---

### Post by quickk on 2011-07-25
Hi everyone, 

    I installed a new media drive that I will be using to share with a windows 7 laptop using samba.  

After days of frustration, I figured out that the sharing is not working because I have to set the permissions for the NTFS drive when it is mounted.   Once it is mounted, using chmod, chown or right-clicking in nautilus does not work.   As a result, when I try to access the files from my windows laptop, it keeps saying that it can't find the share (due to the permission issue).  

How do I change the fstab to automatically mount the ntfs drive, and have completely open permissions (read/write/execute by everyone)?

Will this work?

```
UUID=28ASDFGF4AABFA4 /media/media ntfs-3g defaults,blksize=4096,umask=0000 
```

I don't really understand what umask is.

---

### Post by quickk on 2011-07-25
Ok, I think it works now.

From what I understand, the umask numbers are subtracted from the regular permission numbers.  For example, 7777 is usually everything open, and umask 0000 means that things will remain open.  On the other hand, umask 7777 means that the effective permissions are 7777 - 7777 = 0000, which is nobody can read/write/execute.

So my FSTAB entry now looks like:

```
UUID=28ASDFGF4AABFA4 /media/media ntfs-3g defaults,umask=0000,uid=1000 0 2
```

where the uid=1000 ["makes the Linux-user with specified uid or username owner of the mounted share, thereby allowing that user to rename files"]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

Now I can access my samba shares from windows!

---

### Post by raja.genupula on 2011-07-25
solved ? please mark it as solved by clicking at thread tools

---

