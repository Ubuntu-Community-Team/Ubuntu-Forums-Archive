---
title: "Unistalling Programs/Softwares"
date: 2010-01-10
forum: General Help
---

### Post by hirano on 2010-01-10
Help! I have just uninstalled some program in my PC. But some of the programs' traces still exists  and my problem is I cant locate them. What will I do to completely remove these programs?

I tried removing it from the add/remove programs.

---

### Post by lukeiamyourfather on 2010-01-10
This command will remove all traces of a application that were installed by the application package.

```
sudo apt-get purge whateverApplicationYouWant
```

Note the dependencies that were installed (if any) will still remain. Also if you manually created any configuration files or the like those will still remain. Cheers!

---

### Post by hirano on 2010-01-10
Okay ill try that.

But, can i use CCleaner?

---

### Post by portable-linux.com on 2010-01-10
You can use bleachbit it is a tool similar to CCleaner. It has two levels one is the root user and the other is the normal user. Go to the root user Bleach Bit and select everything. It will remove all the unnecessary files and folders in the system as well as in the temporary directory.

---

