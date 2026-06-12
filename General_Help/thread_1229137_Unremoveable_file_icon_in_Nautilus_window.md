---
title: "Unremoveable file icon in Nautilus window"
date: 2009-08-01
forum: General Help
---

### Post by DGeeez on 2009-08-01
About a month ago, when I was still distro-hopping, I was trying to store large files (like movies) in a separate partition which could be accessed by different distros and Windows. This didn't really turn out so well, as I spent lots of time creating and adjusting partition sizes, and then the transfer of files to and from partitions like fat32 was unbelievably slow. It's also how I found out that fat32 cannot handle files which are larger than 4GB, and that's probably how I ended up with a ghost entry for one of those files in Nautilus. I cannot delete it through Nautilus, because it's a link to a nonexistent file, so (not surprisingly) the rm command in Terminal didn't work for me either for this reason. But the entry is still taking up space in my home folder, and I hope there's some way of getting rid of it. Anybody know how to deal with this?

Thanks.

---

### Post by michy99 on 2009-08-01
What is the output of these commands? Substitute the name of the file for NAMEOFFILE.```
ls -l ~/NAMEOFFILE
lsattr ~/NAMEOFFILE
```

---

### Post by DGeeez on 2009-08-01
> **michy99 said:**
> What is the output of these commands? Substitute the name of the file for NAMEOFFILE.```
ls -l ~/NAMEOFFILE
lsattr ~/NAMEOFFILE[
```/quote]

The output for this command was ```
mrg@mrg-desktop:~$ ls -l ~/Star_Trek_II
ls: cannot open directory /home/mrg/Star_Trek_II: Permission denied

```

[QUOTE=michy99;7717958]```
lsattr ~/NAMEOFFILE
```
```
lsattr ~/Star_Trek_II
```
This did not produce any output, just the next command prompt.

---

### Post by michy99 on 2009-08-01
Well then, we'll just get a bigger hammer.```
sudo ls -l ~/Star_Trek_II

sudo lsattr ~/Star_Trek_II
```

---

### Post by DGeeez on 2009-08-02
> **michy99 said:**
> Well then, we'll just get a bigger hammer.```
sudo ls -l ~/Star_Trek_II

sudo lsattr ~/Star_Trek_II
```

Guess I should of thought of that! The output is ```
mrg@mrg-desktop:~$ sudo ls ~/Star_Trek_II
[sudo] password for mrg: 
STARTRAK.ISO
mrg@mrg-desktop:~$ sudo lsattr ~/Star_Trek_II
------------------- /home/mrg/Star_Trek_II/STARTRAK.ISO

```

Should I try and remove this - what is it, anyway?

---

### Post by michy99 on 2009-08-02
So Star_Trek_II is a folder whick contains STARTRAK.ISO. This should get rid of it:```
sudo rm -r ~/Star_Trek_II
```

---

### Post by DGeeez on 2009-08-02
> **michy99 said:**
> So Star_Trek_II is a folder whick contains STARTRAK.ISO. This should get rid of it:```
sudo rm -r ~/Star_Trek_II
```

Yay, it's gone!

Thanks!:D

---

