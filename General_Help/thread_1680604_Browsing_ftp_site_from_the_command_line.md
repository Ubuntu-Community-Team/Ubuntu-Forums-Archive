---
title: "Browsing ftp site from the command line"
date: 2011-02-02
forum: General Help
---

### Post by towheedm on 2011-02-02
Is there a way to browse the files and directories on an ftp site from the command line similar to how you browse your local directories and files?

---

### Post by ragtag on 2011-02-02
Just do:

```
ftp yoursite.com
```

And login. It's a basic ftp client. Type ? or help, for help.

You can also install something like ncftp, which is considerably more powerful command line ftp program.

---

### Post by towheedm on 2011-02-02
Great, it works.  Will install ncftp and give it a try.  Thanks.

---

### Post by gmargo on 2011-02-03
Also give **lftp(1)** a try.

---

### Post by towheedm on 2011-02-03
> **gmargo said:**
> Also give **lftp(1)** a try.

Will do, thanks.

---

