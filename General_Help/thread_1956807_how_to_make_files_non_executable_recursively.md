---
title: "how to make files non executable recursively?"
date: 2012-04-11
forum: General Help
---

### Post by sohlinux on 2012-04-11
Hello,

How can I make all files in a directory and all its sub directories non executable?

thanks

---

### Post by roelforg on 2012-04-11
```

chmod -R -x /path/to/dir

```

---

### Post by sohlinux on 2012-04-11
> **roelforg said:**
> ```

chmod -R -x /path/to/dir

```

thanks that worked! but I have many symbolic linked files in those directories, do you know how to follow the symbolic links and chmod?

:)

---

### Post by roelforg on 2012-04-11
> **sohlinux said:**
> thanks that worked! but I have many symbolic linked files in those directories, do you know how to follow the symbolic links and chmod?

:)

```

find /path/to/dir -follow -exec "chmod -x {}"

```
I believe.

---

### Post by sisco311 on 2012-04-11
> **roelforg said:**
> ```

find /path/to/dir -follow **-type f** -exec "chmod -x {}"

```
I believe.

Fixed. :)

*Execute* is needed on a directory to access the "inode" information of the files within.

---

### Post by sohlinux on 2012-04-11
> **sisco311 said:**
> Fixed. :)

*Execute* is needed on a directory to access the "inode" information of the files within.

thanks! :p:p:p

---

