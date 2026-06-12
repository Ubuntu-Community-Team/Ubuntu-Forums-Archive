---
title: "Hard link multiple files"
date: 2011-01-14
forum: General Help
---

### Post by COKEDUDE on 2011-01-14
Is it possible to hard link multiple files at the same time? I tried to use wildcards with no luck. This is what I tried.

```
ln /home/hardlink/* /home/hardlink1
```

---

### Post by Vaphell on 2011-01-14
you can go around it by using a loop

```
for stuff in /home/hardlink/*; do ln "$stuff" /home/hardlink1; done;
```

and why exactly do you need hardlinks? where is the benefit?

---

### Post by vanadium on 2011-01-14
You can only have one hardlink refer to one file (which in it own is also a hardlink).

You can link multiple files to another place in one go with a constuction such as:

```

cd /home/hardlink/
for f in * ;  do ln "$f" /home ;  done

```
This will create hardlinks in the destination /home with the same names as in the original directory. No hard links are allowed for directories: you will receive messages for directories.

[edit] The more direct approach of Vaphell with directly specifying full pathnames does work.

---

### Post by COKEDUDE on 2011-01-14
> **Vaphell said:**
> you can go around it by using a loop

```
for stuff in /home/hardlink/*; do ln "$stuff" /home/hardlink1; done;
```

and why exactly do you need hardlinks? where is the benefit?

Thank you for that. 

The reason I am doing this is because I am sharing some work with other people and I don't want them to be able to delete my copy. I want to be able to see whatever they add my work so hard linking is the best way I know of to do this. 

> **vanadium said:**
> You can only have one hardlink refer to one file (which in it own is also a hardlink).

You can link multiple files to another place in one go with a constuction such as:

```

cd /home/hardlink/
for f in * ;  do ln "$f" /home ;  done

```
This will create hardlinks in the destination /home with the same names as in the original directory. No hard links are allowed for directories: you will receive messages for directories.

[edit] The more direct approach of Vaphell with directly specifying full pathnames does work.

Thank you. This also works.

---

### Post by James78 on 2011-01-14
> **COKEDUDE said:**
> Thank you for that. 

The reason I am doing this is because **I am sharing some work with other people and I don't want them to be able to delete my copy.** I want to be able to see whatever they add my work so hard linking is the best way I know of to do this.
You could also set in the permissions that they can't delete the files (by removing the write bit, which will also stop them from changing anything inside your work). But hard linking is another good way, when hard linking, if you modify the hard links files contents, it still modifies the original file, just like it does with soft linking (in case you thought different than that).

> **vanadium said:**
> You can only have one hardlink refer to one file (which in it own is also a hardlink).
I just made a file, made 2 hard links to the same file, used both the hard links, and the original file, and everything worked fine ...

---

### Post by sisco311 on 2011-01-14
> **COKEDUDE said:**
> Thank you for that. 

The reason I am doing this is because I am sharing some work with other people and I don't want them to be able to delete my copy. I want to be able to see whatever they add my work so hard linking is the best way I know of to do this. 



You can set the sticky bit on the shared directory. If the sticky bit is set on the directory, only the owner of a file or the owner of the directory (and the super-user of course) will be able to delete that file.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by sisco311 on 2011-01-14
> **COKEDUDE said:**
> Thank you for that. 

The reason I am doing this is because I am sharing some work with other people and I don't want them to be able to delete my copy. I want to be able to see whatever they add my work so hard linking is the best way I know of to do this. 



You can set the sticky bit on the shared directory. If the sticky bit is set on the directory, only the owner of a file or the owner of the directory (and the super-user of course) will be able to delete that file.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by James78 on 2011-01-14
> **sisco311 said:**
> You can set the sticky bit on the shared directory. If the sticky bit is set on the directory, only the owner of a file or the owner of the directory (and the super-user of course) will be able to delete that file.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Ah yes, I forgot about that! Much much better solution. :D

---

### Post by James78 on 2011-01-14
Double post. :(

---

### Post by James78 on 2011-01-14
Triple post. :(

---

### Post by vanadium on 2011-01-14
> **James78 said:**
> I just made a file, made 2 hard links to the same file, used both the hard links, and the original file, and everything worked fine ...
You indeed can make multiple hardlinks to one single file (technically, all hardlinks you create are equivalent. What I wanted to say, is that you cannot make one hardlink that links to multiple files.

Safeguarding a file against deletion indeed is a very good reason to create hardlinks.

---

### Post by James78 on 2011-01-14
> **vanadium said:**
> You indeed can make multiple hardlinks to one single file (technically, all hardlinks you create are equivalent. What I wanted to say, is that you cannot make one hardlink that links to multiple files.

Safeguarding a file against deletion indeed is a very good reason to create hardlinks.
Ahhhh. I figured I might have misunderstood what you said. Yup, that is indeed true. :)

---

### Post by COKEDUDE on 2011-01-30
> **James78 said:**
> You could also set in the permissions that they can't delete the files **(by removing the write bit, which will also stop them from changing anything inside your work)**. But hard linking is another good way, when hard linking, if you modify the hard links files contents, it still modifies the original file, just like it does with soft linking (in case you thought different than that).


I just made a file, made 2 hard links to the same file, used both the hard links, and the original file, and everything worked fine ...

Were sharing our work so they need to be able to add to my work. So if I took the write bit away then they wouldn't be able to add to my work.

---

