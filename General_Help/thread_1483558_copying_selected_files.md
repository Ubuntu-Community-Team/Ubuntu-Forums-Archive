---
title: "copying selected files"
date: 2010-05-14
forum: General Help
---

### Post by jhapk on 2010-05-14
Hi,

I have to copy and move files over two systems all the time. So when I am on system 1, I simply use the command

```
$scp * system2:/some_directory
```

There are many files in PWD of system1 with different extensions. Of all the files in the PWD on system1, I don't need a file called *residual.dat as it it particularly big and wastes a lot of time copying.

How can I make a shortcut so that every time I do scp, it copies everything but the *residual.dat file?

Thanks

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
[http://www.linuxforums.org/forum/linux-programming-scripting/107805-solved-scp-how-copy-files-recursivly-but-exclude-regex-pattern-download.html](http://www.linuxforums.org/forum/linux-programming-scripting/107805-solved-scp-how-copy-files-recursivly-but-exclude-regex-pattern-download.html)

---

