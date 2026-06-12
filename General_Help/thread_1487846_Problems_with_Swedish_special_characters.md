---
title: "Problems with Swedish special characters"
date: 2010-05-19
forum: General Help
---

### Post by npss84 on 2010-05-19
Hi

I got a problem when I try to open files that contain the special characters åäö. In the file browser it says invalid encoding after the file name, and when I try to open it it says it cant be found. If I try to send a file via yahoo mail it says that I didn't pick a file.

This probably is a common problem, but I didn't manage to find another thread about it.

Some files I can open from a file browser, but I can't attach them to a mail. It seems like it's only newer files with the characters I can't open.

Would be thankful for help

---

### Post by hatchie on 2010-05-31
I too have this problem.  I first notice it when unrar-ing archives with Archive Manager that contain files with such characters.  The characters are not even recognised, when looking through the archive they are just replaced with ´?'.  When extracting, it gives me the error-

"caution: filename not matched:   Bullitts Domin\?.mp3"

The actual filename is Bullitts Dominæ.mp3

Any ideas?

Thanks in advance...

---

### Post by sagredo on 2010-06-08
try to unzip by the terminal

```
unzip 'file.rar'
```

---

### Post by tanas on 2010-10-17
sagredo's workaround worked for me!

I had special characters in the archive name and in the files in it as well.

---

