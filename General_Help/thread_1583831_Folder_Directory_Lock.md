---
title: "Folder Directory Lock"
date: 2010-09-28
forum: General Help
---

### Post by Rotax on 2010-09-28
I don't know what I have done lock Downloads Folder Directory or how did I lock on that folder. How do remove lock or unlock that folder? 
See attach picture.

---

### Post by vamped on 2010-09-28
I looks like either you no longer own the directory, or don't have permission to read it. This can be caused by copying files from another system (just a guess here).

You can fix either easily. From a terminal, type:

```
$ ls -ld ~/Downloads
```

Mine looked like this:
```
drwxr-xr-x 2 robert robert 4096 2010-09-23 22:33 /home/robert/Downloads
```

If you no longer own the directory ( indicated by robert robert above, where robert is my username ) then type:
```
$ sudo chown -R robert:robert ~/Downloads  # replacing robert with your username
```

If your permissions need changing -- if they are not "drwxr-xr-x", then type this:
```
$ chmod 755 ~/Downloads
```

You can read about the commands used above by typing:
```
$ man ls
$ man chown
$ man chmod
$ man sudo
```

---

### Post by rhoparkour on 2010-09-28
And, if you are scared of terminals (it's better to use the command line, though), try this to get a Graphical Interface:

```

sudo nautilus

```

You are now in the window manager as a superuser. Navigate to /home/whateveryourusernameis then right click on Downloads. Look for the permissions tab, and enable yourself read and write privileges...

Good luck.

---

### Post by Rotax on 2010-09-28
Thanks vamped, I have removed Download folder lock. 

So this is solved. 


> **vamped said:**
> I looks like either you no longer own the directory, or don't have permission to read it. This can be caused by copying files from another system (just a guess here).

You can fix either easily. From a terminal, type:

```
$ ls -ld ~/Downloads
```Mine looked like this:
```
drwxr-xr-x 2 robert robert 4096 2010-09-23 22:33 /home/robert/Downloads
```If you no longer own the directory ( indicated by robert robert above, where robert is my username ) then type:
```
$ sudo chown -R robert:robert ~/Downloads  # replacing robert with your username
```If your permissions need changing -- if they are not "drwxr-xr-x", then type this:
```
$ chmod 755 ~/Downloads
```You can read about the commands used above by typing:
```
$ man ls
$ man chown
$ man chmod
$ man sudo
```

---

