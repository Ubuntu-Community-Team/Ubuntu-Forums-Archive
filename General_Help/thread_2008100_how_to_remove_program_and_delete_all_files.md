---
title: "how to remove program and delete all files"
date: 2012-06-22
forum: General Help
---

### Post by famebu on 2012-06-22
Hello,
How can you remove a program and all the files I did:

```
sudo apt-get purge remove quassel
```

That removed the program but when I reinstalled it all the files and changes to the program were still there.

---

### Post by papibe on 2012-06-22
Hi famebu.

'remove' conflicts with 'purge'.

'remove' leaves the configuration files, but 'purge' will remove them.

In your case, you need to use just the 'purge' option.

Regards

---

### Post by oldos2er on 2012-06-22
If quassel creates any config files or folders in your home folder, you will need to manually delete those.

---

