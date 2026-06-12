---
title: "Chmod issue"
date: 2010-04-02
forum: General Help
---

### Post by Parsa86 on 2010-04-02
Hi,
I have a samba server setup on my ubuntu, and shared two folders there using nautilus. From my other computer I can only access one of these though. The other one seems to not allow guest, even though I have selected share with guests for both.

I did **ls -l** for both and this is what I get:

drwx------ 1 Parsa Parsa 86016 2010-04-01 13:10 Folder1
drwxrwxrwx 13 Parsa Parsa 4096 2010-04-02 20:05 Folder2

Folder 2 is fine, Folder 2 is not. How can I make available Folder1 and all the file/folders inside it? I tried chmod 777 but it didn't do much?!

Many thanks!

---

### Post by akakingess on 2010-04-02
Did you add the -R to make it recursive, as in the chmod will affect subfolders and files and such? Just a thought...

---

### Post by Parsa86 on 2010-04-02
so I am using:
sudo chmod a=rwx folder2/

how can I add recursive? sorry can't figure it out!

---

### Post by kambrik on 2010-04-02
If you want folder 1 and all sub folders to be rw then do

```
sudo chmod -R 0777
```

You need to look up the meaning of this (drwxrwxrwx).  Knowing this will help you in the future to understand what permission are set on the folder/file.

d - directory
rwx - owner - Read,Write,Execute
rwx - group - Read,Write,Execute
rwx - other - Read,Write,Execute

Hope this helps

---

### Post by Parsa86 on 2010-04-02
That's great thanks! however it still isn't accessible on my other PC and when I ls -l it still gives 
drwx------ 

Any solutions? cheers

---

### Post by whiteychs on 2010-04-02
```
sudo chown -R username Folder2
sudo chmod -R 777 Folder2
```

Restart your PCs or just the samba server

---

