---
title: "Permision Denied..."
date: 2009-09-06
forum: General Help
---

### Post by akromm on 2009-09-06
So im developing an application in Eclipse using c++,  I have all the files on a seperate drive (mounted to /media/disk ) which is an ntfs file system.  Up until recently it worked fine...  But now, it all works fine, it compiles and links and generates the executable.  But then when i go to run the program i get this error.

```

.../Debug$ ./WarTornlinux 
bash: ./WarTornlinux: Permission denied

```

not sure if it has anything to do with it, but the drive gets mounted as root (owner and group) but i get the same error message even if i try to run it as root.  I tried chowning it but that didnt work either. (it stayed as root and still wouldnt run)... any other ideas?

---

### Post by akromm on 2009-09-07
nobody?

---

### Post by scragar on 2009-09-07
```
chmod +x WarTornlinux
```

---

### Post by akromm on 2009-09-08
i did that and it didnt work.  its permissions are -rwxrwxrwx

---

