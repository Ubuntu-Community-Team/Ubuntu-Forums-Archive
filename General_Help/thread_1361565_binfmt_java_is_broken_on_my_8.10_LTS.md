---
title: "binfmt java is broken on my 8.10 LTS"
date: 2009-12-22
forum: General Help
---

### Post by beric on 2009-12-22
Hello.
I'm trying to activate binfmt support for java.
I'm using binfmt-support
I did /etc/init.d/binfmt-support start.
binfmts shows:
```

update-binfmts --display
python2.5 (enabled):
     package = python2.5
        type = magic
      offset = 0
       magic = \xb3\xf2\x0d\x0a
        mask =
 interpreter = /usr/bin/python2.5
    detector =
jar (enabled):
     package = sun-java6
        type = magic
      offset = 0
       magic = PK\x03\x04
        mask =
 interpreter = /usr/lib/jvm/java-6-sun-1.6.0.17/jre/lib/jexec
    detector =

```but still when I try to run my jar ./myapp.jar I get the follwing error:
```
 invalid file (bad magic number): Exec format error.
```of curse when I invoke my jar with java --jar  everything runs fine.

---

