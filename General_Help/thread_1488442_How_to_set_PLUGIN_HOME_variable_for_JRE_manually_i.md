---
title: "How to set PLUGIN_HOME variable for JRE manually installed"
date: 2010-05-20
forum: General Help
---

### Post by deepclutch on 2010-05-20
Hello,
I've JRE 7 manually installed to /opt/jre1.7.0  directory.
I  have following lines in /etc/profile :
```
export PATH=$PATH:/opt/jre1.7.0/bin
export JAVA_HOME=/opt/jre1.7.0/bin/java
export PLUGIN_HOME=/opt/jre1.7.0/lib/

```
This does not work with java_vm :
```
java_vm process: You need to set both JAVA_HOME and PLUGIN_HOME
```Where PLUGIN_HOME is to be Pointed to?

If I set :
```
PLUGIN_HOME=/opt/jre1.7.0/lib/amd64/libnpjp2.so
```

It errors out:
```
java_vm process: could not find Java VM symbols
```

---

