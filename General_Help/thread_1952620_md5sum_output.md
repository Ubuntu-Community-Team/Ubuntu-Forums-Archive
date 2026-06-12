---
title: "md5sum output"
date: 2012-04-04
forum: General Help
---

### Post by ukchris on 2012-04-04
Hi folks,

When running the md5sum function from the terminal the returned output includes the checksum and the filename (or file path and name if called from a script).

So if I run:

```
md5sum filename.extension
```

I get the following output:

```
0b82b43abeeec299ba9f56d6e3dc03a0  filename.extension
```

Is it possible to suppress the filename (or filepath/name) element of this output so I just get the following?

```
0b82b43abeeec299ba9f56d6e3dc03a0
```

Thanks in advance for any help.

---

### Post by brainwash on 2012-04-04
You can split the output using the **cut** command:
```
md5sum filename.extension | cut -d" " -f1
```

Read the manual page for more information:
```
man cut
```

---

### Post by ukchris on 2012-04-04
Thanks brainwash.  That works perfectly.  :)

---

