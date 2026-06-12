---
title: "Accessing Windows C Drive in Ubuntu"
date: 2010-06-11
forum: General Help
---

### Post by bastianbux on 2010-06-11
I was able to easily do so when trying Ubuntu out on the Live CD, but now that I've installed Ubuntu as a windows program and am inside it, I can't seem to find access to my old Windows files. How do I access them? 

Thanks!

---

### Post by X-Windows on 2010-06-11
What do you mean by "as a windows program"? If you did a normal dual-boot install the "Ubuntu restricted extras package" from Ubuntu Software Center, I believe that has the NTFS file system read/write package included.

---

### Post by JayKay3000 on 2010-06-11
If you mean you used wubi to install it within windows as an application then your files will be located under a directory called /host or under /media. (probably /host)

I think these can be found under File System.

Sorry. It's a been a while now since I used wubi. Hope that helps.

Here is a nice little guide installing and about wubi

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by jarviser on 2010-06-11
Deleted

---

### Post by bastianbux on 2010-06-11
> **JayKay3000 said:**
> If you mean you used wubi to install it within windows as an application then your files will be located under a directory called /host or under /media. (probably /host)

I think these can be found under File System.

Sorry. It's a been a while now since I used wubi. Hope that helps.

Here is a nice little guide installing and about wubi

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

"Host" it is! Thank you so much!

---

