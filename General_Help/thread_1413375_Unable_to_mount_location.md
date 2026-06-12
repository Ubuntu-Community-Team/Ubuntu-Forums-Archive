---
title: "Unable to mount location"
date: 2010-02-22
forum: General Help
---

### Post by DogWalker on 2010-02-22
I have some shared folders on my laptop, most of which I can access from any other machine in the house.  But one returns an error every time from any PC.  I open the Places menu, select network, choose the machine and get a set of shared folders.  But when I try to open this one I get an error message "Unable to mount location.  Failed to mount Windows Share".  All the machines are running Ubuntu 9.04 or better.  No problem with any other shared folder, and the permissions are the same for all.

Can anyone suggest the cause of the problem and a solution?  I worked around it by creating another folder, copying everything across, and sharing it with the usual perfect result.  But knowing what the issue is will teach me more.

Ollie K

---

### Post by steviefordi on 2010-02-22
Try mounting it from the command line with mount.cifs or gvfs-mount. This may give you some error messages that you weren't seeing through the GUI.

I can't remember the exact syntax but I think it goes something like:

```
mount.cifs //machine/sharename /folder/to/mount/in
```

You can use -o to pass a username and password to the machine with the share. See the man page (man mount.cifs) for more details.

For gvfs-mount, I think you just give the share that you want to mount, and it creates a mount point for you:

```
gvfs-mount //machine/sharename
```

Let us know how you get on.

---

### Post by DogWalker on 2010-02-22
Thanks for the help.  I didn't find anything sufficiently and quickly intelligible for mount.cifs syntax.  But when I tried gvfs.mount I got exactly the same results as with the GUI: success on all folders except one, and the same error message when I tried the folder that I could not mount before.  So, I know from the successes that I was doing it correctly, and therefore I deduce there is something, but as yet unknown, wrong with the problem folder.

I have some stuff I have to give priority to, but I plan to get back to this tomorrow afternoon with a little more leisure.

---

