---
title: "cannot chdir from ...."
date: 2011-04-05
forum: General Help
---

### Post by dmolina87 on 2011-04-05
Hello, I'm trying to delete a folder and I have this problem:

rm -dfr festival/
rm: cannot chdir from `festival/' to `config': Permission denied

I don't know how to delete it

Thank you

---

### Post by DeMus on 2011-04-05
> **dmolina87 said:**
> Hello, I'm trying to delete a folder and I have this problem:

rm -dfr festival/
rm: cannot chdir from `festival/' to `config': Permission denied

I don't know how to delete it

Thank you

To delete a folder use rmdir (type rmdir --help) for assistance about parameters.
With rm there is no option -d possible. At least not to the help I looked into.

---

### Post by 3Miro on 2011-04-05
What folder are you trying to delete.

```
rm -fr folder_name
```
will delete the folder and all of its sub-folders, however, you don't have the right permissions to do that. You can use
```
sudo rm -fr folder_name
``` 
however, THIS IS A VERY BRUTAL COMMAND AND IT CAN POTENTIALLY ERASE IMPORTANT FILES FORM YOUR SYSTEM, YOU CAN TOTALLY DESTROY YOUR SYSTEM THAT WAY. This command is only a step short of "format c:".

---

### Post by dmolina87 on 2011-04-05
I think that my problem is not with RM or RMDIR, the problem is with the directory...CD or CHDIR

I cannot use RMDIR because the folder is not empty, It has another folder inside (config) which I can delete

I think that I need to change de directory of this folder, but I don't know how...

---

### Post by 3Miro on 2011-04-05
> **dmolina87 said:**
> I think that my problem is not with RM or RMDIR, the problem is with the directory...CD or CHDIR

I cannot use RMDIR because the folder is not empty, It has another folder inside (config) which I can delete

I think that I need to change de directory of this folder, but I don't know how...

rm with the options -fr and sudo in front should do the trick. However, really make sure you don't need this folder.

Another option is to use the file manager in super-user mode:
```
gksudo nautilus
```

However, this is also dangerous as you will be allowed to directly mess with parts of your system that you shouldn't normally be allowed to. Be very careful what you do.

---

