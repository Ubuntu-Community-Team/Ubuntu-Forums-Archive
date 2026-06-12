---
title: "Uncompress .tar.xz"
date: 2011-05-01
forum: General Help
---

### Post by aravindreddy on 2011-05-01
Hello All

I am trying to uncompress a .tar.xz file.

Can somebody suggest me a command as tar -Jxf <filename> gives me an error.

anusha@anusha-laptop:/usr/src/gcc-4.4$ tar -Jxf gcc-4.4.3.tar.xz 
tar: xz: Cannot exec: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Thanks,
Aravind.

---

### Post by wojox on 2011-05-01
You can man xz to see your options.

Drop the tar and use:

```
xz -dl <filename>
```


Then use tar. :P

---

### Post by carlexpc on 2012-01-26
use the command:

**unxz** *<file.tar.xz>*

then use tar to decompress.

---

### Post by dargaud on 2012-01-26
unxz -c file.tar.xz | tar xv

---

### Post by vcrpcant on 2012-11-02
Open synaptic and check if you've got installed:
xz-utils
If not, install it.

If you want you may do this in terminal:
sudo apt-get update
sudo apt-get install xz-utils

then, right-click and extract
or, in terminal:
$ tar -Jxf [filename]

---

