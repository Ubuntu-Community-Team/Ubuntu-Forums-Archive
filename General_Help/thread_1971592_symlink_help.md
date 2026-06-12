---
title: "symlink help"
date: 2012-05-02
forum: General Help
---

### Post by OldManRiver on 2012-05-02
All,

Hardly ever use a symlink and move all the mail files and programs to a directory on a new mail server.  To see the directory as a local directory I know I have to mount and then symlink the directory.  I am having 2 problems with this.
[LIST=1]
[*]The fstab file is not being read at boot-up,
[*]My syntax is not right for the symlink so the files are not read.
[/LIST]
Have my symlink of:
```
ln -s -t /mysource /mytarget
```
What is wrong with my code and why doesn't fstab run?

Thanks!

OMR

---

### Post by mendhak on 2012-05-02
Can you edit your post and show us the relevant lines from your fstab?

---

### Post by OldManRiver on 2012-05-02
> **mendhak said:**
> Can you edit your post and show us the relevant lines from your fstab?

This is the line for this share
```

//localpath/mail smb://serverpath/TBird smbfs credentials=/home/myuser/.smbcredentials,uid=1000,gid=1000 
```

It links correctly when we run "mount -lsa" manually from the terminal.

Thanks!

OMR

---

### Post by Derek Karpinski on 2012-05-02
Can you try changing 'smbfs' to 'cifs'?

Here's a great resource:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

if you try 'sudo mount -lav' (without the sloppy flag) what's the output?

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #2 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

