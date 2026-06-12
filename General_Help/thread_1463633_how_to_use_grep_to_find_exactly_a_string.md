---
title: "how to use grep to find exactly a string"
date: 2010-04-27
forum: General Help
---

### Post by smartlogicsseo on 2010-04-27
How to search for exact phrase using grep ?
e.g root:rootadministrator:123root:
the grep command should see for exact phrase i.e. root
its default beaviour is that it finds every other string in which there is root.

---

### Post by TheSqueak on 2010-04-27
grep "^STRING$" filename

The "^" means match the beginning of the line, and the $ means match the end of the line, so it will only return lines which exactly match the string you're looking for

---

### Post by smartlogicsseo on 2010-04-27
Thanks

---

### Post by Elfy on 2010-04-27
[http://art.ubuntuforums.org/showpost.php?p=4465816&postcount=1](http://art.ubuntuforums.org/showpost.php?p=4465816&postcount=1)

---

