---
title: "SWIG not finding PHP"
date: 2009-11-04
forum: General Help
---

### Post by KayakJim on 2009-11-04
I have an Ubuntu 8.04 Hardy server and have download some c functions that use SWIG to build bindings for other languages.

When I run ./configure I receive the following:
```
checking for swig... swig
checking for swig >= 1.3.33... 1.3.33
checking for mcs... no
checking for gmcs... no
checking for java... java
checking for javac... no
checking for /usr/lib/perl/5.8/CORE/perl.h... yes
checking for php... php
checking for /usr/local/include/php/main/php.h... no
checking for /usr/local/include/php/Zend/zend.h... no
checking for /usr/include/php/main/php.h... no
checking for /usr/include/php/Zend/zend.h... no
checking for /opt/local/include/php/main/php.h... no
checking for /opt/local/include/php/Zend/zend.h... no
checking for /opt/local/php/main/php.h... no
checking for /opt/local/php/Zend/zend.h... no
checking for python... python
checking for /usr/include/python2.5/Python.h... yes
checking for ruby... ruby
checking for /usr/lib/ruby/1.8/x86_64-linux/ruby.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating project/build/Doxyfile
config.status: creating librets-config
config.status: creating librets-config-inplace
config.status: creating project/librets/src/config.h
config.status: project/librets/src/config.h is unchanged

Option summary:

Use ccache .................: no
Use dependency checking ....: no
Use -fPIC...................: yes
Use shared dependencies.....: no
Compile type................: Normal
Compile examples............: no
Compile SQL compiler........: yes
Compile SWIG bindings.......: yes
  With CSharp...............: no
  With Java.................: no
  With PERL.................: yes
  With PHP..................: no
  With Python...............: yes
  With Ruby.................: no
Enable Maintainer Docs......: no

```

I do have php5, php5-cli, and php5-dev installed so I'm not sure why PHP is not be detected and the bindings built.

Any suggestions on what is missing?

---

### Post by KayakJim on 2009-11-04
For anyone else having the same problem, the fix is to create a symlink for /usr/local/include/php that points to /usr/local/include/php5

I hope this helps someone.

---

