---
title: "Configure Eclipse PDT with Zend Debugger"
date: 2011-04-14
forum: General Help
---

### Post by nate91 on 2011-04-14
I've been using Eclipse PDT with Zend Debugger to debug my PHP web scripts for a while, but after installing Ubuntu 10.04, I've been having issues setting up the development environment again.

I have installed Apache 2.2.16 and PHP 5.2.14 manually.

Eclipse was installed from the Synaptic Package Manager.  I installed the Zend debugger and PDT for Eclipse under Eclipse's Help -> Install New Software.

Yet whenever I try to debug a web script it executes the script without stopping at any of my breakpoints.  The debug window immediately shows the debug session terminated.

The end of my php.ini file located in /usr/local/lib says:
```

[Zend]
zend_extention=/home/nathan/ZendDebugger.so
zend_debugger.allow_hosts=127.0.0.1
zend_debugger.expose_remotely=always

```I obtained the .so file via
```
cp ~/.eclipse/org.eclipse.platform_3.5.0_155965261/plugins/org.zend.php.debug.debugger.linux.x86_64_5.3.18.v20100905/resources/php5/ZendDebugger.so ~
```Any ideas?

---

### Post by nate91 on 2011-04-19
Fixed it.  Turns out it's spelled "extension" not "extention"

---

