---
title: "java.util.zip.ZipException when loading JNLP"
date: 2010-10-13
forum: General Help
---

### Post by skeet625 on 2010-10-13
I am trying to run a jnlp file from Ubuntu 10.10.  I can run it from Windows but whenever I try to load it from Ubuntu I get the following error and then it acts like it doesn't have any of the dependency jars.

My guess is it has a problem with the certificates.

Has anyone seen this before?

```
java.util.zip.ZipException: error in opening zip file
    at java.util.zip.ZipFile.open(Native Method)
    at java.util.zip.ZipFile.<init>(ZipFile.java:131)
    at java.util.jar.JarFile.<init>(JarFile.java:150)
    at java.util.jar.JarFile.<init>(JarFile.java:101)
    at net.sourceforge.jnlp.tools.JarSigner.verifyJar(JarSigner.java:250)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader$1.run(JNLPClassLoader.java:657)
    at java.security.AccessController.doPrivileged(Native Method)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.activateJars(JNLPClassLoader.java:72:cool:
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:453)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:16:cool:
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:641)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:420)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:732)
```

---

