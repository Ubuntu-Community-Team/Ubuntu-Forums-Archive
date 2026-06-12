---
title: "Infinite directory loop"
date: 2012-03-31
forum: General Help
---

### Post by chocoboman on 2012-03-31
Basically, the file path is like /media/Elements/.whatever/file/file/file/file/[...] and goes on forever.

I tried rm -rf but did not solve it.

It gives me a warning about "Circular directory structure" and does not delete the loop folder.

Any help?

---

### Post by HiImTye on 2012-03-31
try
```
sudo rm -f /path/
```

---

### Post by chocoboman on 2012-03-31
> **HiImTye said:**
> try
```
sudo rm -f /path/
```

"Cannot remove: is a directory".

---

### Post by HiImTye on 2012-03-31
sorry, add -R

---

### Post by lisati on 2012-03-31
> **chocoboman said:**
> "Cannot remove: is a directory".

Try without a trailing "/".....

---

### Post by chocoboman on 2012-03-31
> **lisati said:**
> Try without a trailing "/".....
Nothing changes.

And rm -Rf gives me the "Circular directory structure" error.

---

### Post by HiImTye on 2012-03-31
make sure that you are deleting the top folder (the first instance of the loop)

---

### Post by chocoboman on 2012-03-31
> **HiImTye said:**
> make sure that you are deleting the top folder (the first instance of the loop)
OK, I had a lot of problems in finding the top folder, cause ther were multiple loops (screw that).

Anyway I deleted them one by one and finally I did it.
Thanks a lot.

---

### Post by Thewhistlingwind on 2012-03-31
> **chocoboman said:**
> OK, I had a lot of problems in finding the top folder, cause ther were multiple loops (screw that).

Anyway I deleted them one by one and finally I did it.
Thanks a lot.

When a support issue is finished. Please set the thread category to "solved" in the edit menu.

---

