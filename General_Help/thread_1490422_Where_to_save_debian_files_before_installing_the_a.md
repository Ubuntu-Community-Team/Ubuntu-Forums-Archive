---
title: "Where to save debian files before installing the app?"
date: 2010-05-22
forum: General Help
---

### Post by alittlemorered on 2010-05-22
Hi

If i want to install packages from debian files, where should i save the debian files when extracting?
For example, i want to install SciLab: I have the compressed debian downloaded in "Downloads". When i extract it so that it can be installed, where should i extract it to?

Thanks. Loving Linux!
J.

I'm running Ubuntu 9.10.

---

### Post by marbss on 2010-05-22
usually i just save make a temp folder in downloads and then extract to it.

---

### Post by ssj6akshat on 2010-05-22
If you want to install .deb files you can save them anywhere and double-click to install them.

---

### Post by marbss on 2010-05-22
> **ssj6akshat said:**
> If you want to install .deb files you can save them anywhere and double-click to install them.

+1  ssj6akshat is correct.

if you mean compressed tar/zip/rar files then just make a temp directory

---

### Post by alittlemorered on 2010-05-22
It won't leave residual files in the folder after installation that i can't delete later? I'm trying to keep the file system tidy. Lived in, but tidy.

---

### Post by gmargo on 2010-05-22
To install a debian package from the .deb file, use the **dpkg(1)** command.
```

sudo dpkg -i file.deb

```But if it's SciLab, what's wrong with the version already available in the repository?

---

