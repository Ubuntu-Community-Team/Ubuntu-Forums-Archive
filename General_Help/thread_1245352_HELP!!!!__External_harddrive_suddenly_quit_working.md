---
title: "HELP!!!!  External harddrive suddenly quit working."
date: 2009-08-20
forum: General Help
---

### Post by tw081490 on 2009-08-20
I have been using Ubuntu for about 3 months since my XP system crashed. I haven't had any problems with it until about 2 days ago. My external 1TB WD My Book suddenly stopped letting me save/edit files on it. When i go into Properties - Permissions it says that i am the owner of it and Folder Access: Create and delete files, File Access:---. I have tried changing the File Access but it will not let me. I would normally just reformat it but i do not have enough space on my other harddrives to back everything up. 

Hope somebody can help me PLEASE.:)

---

### Post by epsolon77 on 2009-08-20
I hope someone reading this will confirm this as I am not a Linux god.

Have you changed the permissions using the CLI?  If not I would use the CLI to change the permissions on ONLY THOSE FOLDERS to 777 or at least 774, though minimum permissions should be 664 or 660.

The command would be 

```
sudo chmod -R 774 (folder name) 
```

PLEASE NOTE NEVER do this on your working directories.  BE VERY CAREFUL RUNNING THIS COMMAND.  I accedently ran this on my //var/ directory once and my entire install crashed and would not work right.  Do not run this unless someone else confirms I have it correct.

---

### Post by treehouse on 2009-08-20
I'm not sure why it wouldn't let you change permissions if you're the owner. Perhaps try changing the permissions as root?

```

sudo nautilus ~

```
to open a root file navigator(assuming you use nautilus), then go to the properties dialog for the drive from there and see if you can change the file permissions.

---

### Post by epsolon77 on 2009-08-20
> **treehouse said:**
> I'm not sure why it wouldn't let you change permissions if you're the owner. Perhaps try changing the permissions as root?

```

sudo nautilus ~

```
to open a root file navigator(assuming you use nautilus), then go to the properties dialog for the drive from there and see if you can change the file permissions.

You may be more comfortable with this method.  I come from Dos and administering a Microsoft network through command line as much as I can, so I prefer the CLI approach.  This method may be safer if you are not comfortable with the Command Line.

---

### Post by tw081490 on 2009-08-20
I have tried *treehouse*s method and it still will not work right.

epsolon77 I do not feel comfortable using the terminal for this job. I have used it many times before, but I have no way to back up my nearly full TB and do not want to lose all my files (home videos, school projects, legal documents, etc.....).

I just found a stack of blank DVDs so I am going to back up as much as possible and format it. If that doesnt work I hope somebody else can come up with a solution. It would be greatly appreciated.

---

### Post by epsolon77 on 2009-08-21
> **tw081490 said:**
> I have tried *treehouse*s method and it still will not work right.

epsolon77 I do not feel comfortable using the terminal for this job. I have used it many times before, but I have no way to back up my nearly full TB and do not want to lose all my files (home videos, school projects, legal documents, etc.....).

I just found a stack of blank DVDs so I am going to back up as much as possible and format it. If that doesnt work I hope somebody else can come up with a solution. It would be greatly appreciated.

Thank you for admiting when you are not comfortable, this is a good thing.  Trust your instincts.  For the record though, my method would not corrupt the data on the external drive.  However if done on the system folders would make your operating system unusable.  Your data would still be there though.  Just clarifying becuase it is important to know the dangers.

And just to clarify, the point to treehouse and my methods are the same, to set the File Access to Read and Write for whatever user or group you use.

---

