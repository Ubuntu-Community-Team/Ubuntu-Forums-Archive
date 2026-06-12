---
title: "chkdupexe - dangling symlinks and duplicately named binaries"
date: 2010-02-10
forum: General Help
---

### Post by HotForLinux on 2010-02-10
What should be done with these dangling symlinks and duplicately named binaries?


[FONT=Courier New]***$chkdupexe ***
Dangling symlink: /usr/bin/mmencode
Dangling symlink: /usr/bin/movemail
Dangling symlink: /usr/bin/javadoc
-rwxr-xr-x 1 root root   466 2009-12-10 16:55 /sbin/update-grub
-rwxr-xr-x 1 root root 40343 2009-12-10 16:54 /usr/sbin/update-grub
-rwxr-xr-x 1 root root 22948 2008-07-09 19:23 /usr/bin/pcregrep
-rwxr-xr-x 1 root root 29391 2007-11-27 17:42 /usr/local/bin/pcregrep
-rwxr-xr-x 1 root root 38876 2008-07-09 19:23 /usr/bin/pcretest
-rwxr-xr-x 1 root root 42300 2007-11-27 17:42 /usr/local/bin/pcretest
-rwxr-xr-x 1 root root   375 2009-12-10 16:55 /sbin/grub-install
-rwxr-xr-x 1 root root 16593 2009-12-10 16:55 /usr/sbin/grub-install[/FONT]

---

### Post by doas777 on 2010-02-10
based on the nature of the files you have listed, i would say absolutely nothing. if you have to ask, then leave them alone.

---

### Post by HotForLinux on 2010-02-10
Based on the nature? .. What do you mean? .. That these files are never used?
What are the duplicates (the ones that are not executed by default) for?

It seems to me that some alternatives should point to new versions of the files they were originally pointing to.

---

### Post by doas777 on 2010-02-10
> **HotForLinux said:**
> Based on the nature? .. What do you mean? .. That these files are never used?
What are the duplicates (the ones that are not executed by default) for?

It seems to me that some alternatives should point to new versions of the files they were originally pointing to.
they are all system files. generally you should really know what you are doing (eg, no need to ask) if you want to remove them.

---

### Post by HotForLinux on 2010-02-10
> **doas777 said:**
> they are all system files. generally you should really know what you are doing (eg, no need to ask) if you want to remove them.

Yes, they are system files. That's why I ask. I wouldn't ask for my files.

---

