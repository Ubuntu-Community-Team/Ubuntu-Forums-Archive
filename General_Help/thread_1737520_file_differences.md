---
title: "file differences?"
date: 2011-04-23
forum: General Help
---

### Post by qwertyjjj on 2011-04-23
I had a hack on my oscommerce website recently.
I have put in the relevant security patches but I need to check whether the hacker left any code changes in my files.
**What is a good file comparison software for linux?**
I need it to scan though all the current files and folders and compare it the original default oscommerce installation so I can check the code.

---

### Post by HermanAB on 2011-04-23
md5sum is a good method.

Calc the sums of all files and compare.

```
$man md5sum
``` 
will get you going.

---

### Post by jocko on 2011-04-23
Or diff. To see files or folders that are different between two directories:
```
diff /path1 /path2
```
If there are many differences, you may want write the output to a file, or scroll it with less:
```
diff /path1 /path2 > new_file.txt
diff /path1 /path2 | less
```

---

### Post by qwertyjjj on 2011-04-23
Thanks.
I tried out Meld diff viewer for future refernce.
Worked very well comparing folders, highlighting file differences, non existing files, etc.

---

