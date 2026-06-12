---
title: "How to uninstall package that install from compiling tar gz file"
date: 2010-09-16
forum: General Help
---

### Post by plusnplus on 2010-09-16
Hi..,
1. How to uninstall package that install from compiling tar gz file
2. how to stop some service ?

---

### Post by sikander3786 on 2010-09-16
Extract the tar package and it will contain a file named "Read Me" or "Install" with the instruction. See here for details.

[http://ubuntuforums.org/showthread.php?t=235022](http://ubuntuforums.org/showthread.php?t=235022)

[http://ubuntuforums.org/showthread.php?t=806371](http://ubuntuforums.org/showthread.php?t=806371)

For stopping a service,

```

sudo service <service name> stop

```

---

### Post by plusnplus on 2010-09-16
hi..,
1. i run:
sudo make uninstall
in source directory, and i got messsage: "no rule to make target 'uninstall' "
2. anyway to see all service that running ?

thanks for any info/ help

---

### Post by sikander3786 on 2010-09-16
To list all the running services,

```

service --status-all

```

Which exact package did you install? I will recommend that next time you use CheckInstall for installing source packages. It saves you all the efforts when you want to uninstall a package.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by plusnplus on 2010-09-21
Hi..,
i want uninstall kannel.
can someone help how to do that?
i install it from gateway-1.4.1.tar.gz

thanks for any info/ help

---

