---
title: "Truecrypt -&gt; ls: reading directory .: Input/output error"
date: 2012-01-27
forum: General Help
---

### Post by demetriodn on 2012-01-27
Hi there,

I was working with a mounted Truecrypt volume of about 5GB. 
The crypt file was on a ntfs mounted volume.
I had to shutdown the computer, and didn't unmount the crypt I was using.
Now, the directory where the crypt file was saved won't open.

ls returns -> ls: reading directory .: Input/output error

This only happens with this directory.
Couldn't find a solution through the forums, would someone have an idea for recovering the files on that directory?

Thanks

---

### Post by carranty on 2012-01-27
The directory won't open?? I could understand if maybe the truecrypt file wouldn't mount, but the directory it is stored in should be just fine.  Does ls see the folder, but not its contents, i.e. go to the directory it is located in and type

```
ls -l | grep *directory*
``````
ls -l *directory*/
```replacing *directory  *with the actual name of the directory.

Also, have you tried cd ing into it?  What about opening it in nautilus?  Can you not even open it when browsing for the crypt file within truecrypt itself?

---

### Post by demetriodn on 2012-01-27
I can cd into it.
The Input/output error happens when I try to list what is inside it.
"ls -l directory" also rerturns the same message.
The directory is listed in its parent directory.

```
demetrio@demetrio-P430:/media/Dados$ ls -l | grep Downloads
drwxrwxrwx 1 root root     24576 2012-01-27 08:05 Downloads
```

From nautilus I can go into it, but there are no files.
Can't create documents or folders through nautilus inside, pops-up I/O error.
Can't open the crypt with Truecrypt, it was not saving history, so I would have to access the crypt file, which I can't.

---

