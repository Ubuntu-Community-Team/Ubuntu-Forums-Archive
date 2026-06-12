---
title: "opening encrypted folder with cryptkeeper"
date: 2012-02-24
forum: General Help
---

### Post by jfreak_ on 2012-02-24
So I had cryptkeeper in 10.04 and I installed 11.10 a while back. So before while reinstalling, I just copied over the encrypted directory to the new install. So now i want to open that again. I don't know why cryptkeeper is not recognising it (I know I sound vague, feel free to ask details) . What do I do?

---

### Post by 0011235813 on 2012-02-24
> **jfreak_ said:**
> So I had cryptkeeper in 10.04 and I installed 11.10 a while back. So before while reinstalling, I just copied over the encrypted directory to the new install. So now i want to open that again. I don't know why cryptkeeper is not recognising it (I know I sound vague, feel free to ask details) . What do I do?
Try "import new EncFS folder". And anyway, what do you mean by "carried over"? Ubuntu doesn't recognize cryptkeeper partitions by default, since cryptkeeper hides the mount point.

---

### Post by jfreak_ on 2012-02-24
Well I have a ./xyz_encfs folder, which cryptkeeper is not importing.

---

### Post by jfreak_ on 2012-02-26
Bumpety bump.
please guys, if not through cryptkeeper, is there any other way to unencrypt it?

---

### Post by jfreak_ on 2012-04-12
BUMP 
pretty please someone please help

Its my personal diary of the past five years.... I don't want to lose it/

---

### Post by wallaroo on 2012-04-12
What exactly happens when you try to import it, does Cryptkeeper do nothing or say that it's not an encrypted directory.

You could try to mount it manually using encfs in a terminal.

encfs path_to_encrypted_directory path_to_mountpoint
e.g.
```
encfs /home/jfreak/.xyz_encfs /home/jfreak/xyz
```(also make sure that the XML control file inside the directory is present and readable - it should be named something like '.encfs6.xml' - very important, it contains the passworded encryption key).

---

### Post by jfreak_ on 2012-04-12
It asks for the encryption password but then throws an error message.
Fuse : mount point is not empty 
Fuse : if you are sure this safe, use the non empty mount option
Fuse failed

---

### Post by wallaroo on 2012-04-12
That usually means that it's trying to mount the drive to an existing directory that already has data in it.

You can either empty out the mountpoint directory or mount it in a new empty directory when you import it.

---

### Post by jfreak_ on 2012-04-13
Thanks it worked. Except now I don't know how to unmount it. 
Anyway I am marking it as solved.

---

### Post by wallaroo on 2012-04-13
> **jfreak_ said:**
> Thanks it worked. Except now I don't know how to unmount it. 
Anyway I am marking it as solved.

In a terminal ...
```
fusermount -u /fullpath_to_mountpoint

```

---

