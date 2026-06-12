---
title: "Eclipse error at start up"
date: 2012-09-13
forum: General Help
---

### Post by layers on 2012-09-13
I just downloaded the latest stable Eclipse version, because the one in the repositories is freezing. But I get this message after the start up window. What is the problem?
```
!SESSION 2012-09-13 17:28:54.730 -----------------------------------------------
eclipse.buildId=I20120608-1400
java.fullversion=GNU libgcj 4.4.3
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_CA
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2012-09-13 17:29:01.964
!MESSAGE Could not start bundle: org.eclipse.equinox.console
!STACK 0
org.osgi.framework.BundleException: Could not start bundle: org.eclipse.equinox.console
   at org.eclipse.osgi.framework.internal.core.ConsoleManager.checkForConsoleBundle(ConsoleManager.java:217)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:297)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
   at java.lang.reflect.Method.invoke(libgcj.so.10)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.equinox.console.command.adapter.Activator.start() of bundle org.eclipse.equinox.console.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:734)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
   at org.eclipse.osgi.framework.internal.core.ConsoleManager.checkForConsoleBundle(ConsoleManager.java:215)
   ...7 more
Caused by: org.osgi.framework.BundleException: Exception in org.apache.felix.gogo.command.Activator.start() of bundle org.apache.felix.gogo.command.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:734)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
   at org.eclipse.equinox.console.command.adapter.Activator.startBundle(Activator.java:248)
   at org.eclipse.equinox.console.command.adapter.Activator.start(Activator.java:239)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
   at java.security.AccessController.doPrivileged(libgcj.so.10)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
   ...11 more
Caused by: java.lang.NoClassDefFoundError: org.apache.felix.gogo.command.OBR
   at java.lang.Class.initializeClass(libgcj.so.10)
   at org.apache.felix.gogo.command.Activator.start(Activator.java:54)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
   at java.security.AccessController.doPrivileged(libgcj.so.10)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
   ...19 more
Caused by: java.lang.ClassNotFoundException: org.apache.felix.bundlerepository.Repository
   at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:501)
   at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:421)
   at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:107)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   ...23 more
Root exception:
java.lang.NoClassDefFoundError: org.apache.felix.gogo.command.OBR
   at java.lang.Class.initializeClass(libgcj.so.10)
   at org.apache.felix.gogo.command.Activator.start(Activator.java:54)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
   at java.security.AccessController.doPrivileged(libgcj.so.10)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
   at org.eclipse.equinox.console.command.adapter.Activator.startBundle(Activator.java:248)
   at org.eclipse.equinox.console.command.adapter.Activator.start(Activator.java:239)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
   at java.security.AccessController.doPrivileged(libgcj.so.10)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
   at org.eclipse.osgi.framework.internal.core.ConsoleManager.checkForConsoleBundle(ConsoleManager.java:215)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:297)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
   at java.lang.reflect.Method.invoke(libgcj.so.10)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
Caused by: java.lang.ClassNotFoundException: org.apache.felix.bundlerepository.Repository
   at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:501)
   at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:421)
   at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:107)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   ...23 more

!ENTRY org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/javax.servlet.jsp_2.2.0.v201112011158.jar was not resolved.
!SUBENTRY 2 javax.servlet.jsp 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.equinox.http.registry_1.1.200.v20120522-2049.jar was not resolved.
!SUBENTRY 2 org.eclipse.equinox.http.registry 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.equinox.jsp.jasper_1.0.400.v20120522-2049.jar was not resolved.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.jdt.compiler.apt_1.0.500.v20120522-1651.jar was not resolved.
!SUBENTRY 2 org.eclipse.jdt.compiler.apt 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/javax.servlet_3.0.0.v201112011016.jar was not resolved.
!SUBENTRY 2 javax.servlet 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.apache.jasper.glassfish_2.2.2.v201205150955.jar was not resolved.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.equinox.http.servlet_1.1.300.v20120522-1841.jar was not resolved.
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.equinox.jsp.jasper.registry_1.0.300.v20120522-2049.jar was not resolved.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper.registry 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.jdt.apt.pluggable.core_1.0.400.v20120522-1651.jar was not resolved.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:05.142
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:05.142
!MESSAGE Bundle reference:file:plugins/org.eclipse.jdt.compiler.tool_1.0.101.v20120522-1651.jar was not resolved.
!SUBENTRY 2 org.eclipse.jdt.compiler.tool 2 0 2012-09-13 17:29:05.143
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".

!ENTRY org.eclipse.osgi 2 0 2012-09-13 17:29:06.948
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.948
!MESSAGE Bundle com.sun.el_2.2.0.v201108011116 [4] was not resolved.
!SUBENTRY 2 com.sun.el 2 0 2012-09-13 17:29:06.948
!MESSAGE Missing imported package javax.el_2.2.0.
!SUBENTRY 2 com.sun.el 2 0 2012-09-13 17:29:06.948
!MESSAGE Missing imported package javax.servlet.http_2.5.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.948
!MESSAGE Bundle javax.el_2.2.0.v201108011116 [6] was not resolved.
!SUBENTRY 2 javax.el 2 0 2012-09-13 17:29:06.948
!MESSAGE Missing imported package javax.servlet_2.5.0.
!SUBENTRY 2 javax.el 2 0 2012-09-13 17:29:06.948
!MESSAGE Missing imported package javax.servlet.http_2.5.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.949
!MESSAGE Bundle javax.servlet_3.0.0.v201112011016 [8] was not resolved.
!SUBENTRY 2 javax.servlet 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.949
!MESSAGE Bundle javax.servlet.jsp_2.2.0.v201112011158 [9] was not resolved.
!SUBENTRY 2 javax.servlet.jsp 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.el_2.2.0.
!SUBENTRY 2 javax.servlet.jsp 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 javax.servlet.jsp 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 javax.servlet.jsp 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.949
!MESSAGE Bundle org.apache.jasper.glassfish_2.2.2.v201205150955 [21] was not resolved.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.el_2.2.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.descriptor_2.6.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.jsp_2.2.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.jsp.el_2.2.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.jsp.tagext_2.2.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing optionally imported package javax.tools_0.0.0.
!SUBENTRY 2 org.apache.jasper.glassfish 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.949
!MESSAGE Bundle org.eclipse.equinox.http.jetty_3.0.0.v20120522-1841 [91] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet_[2.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package javax.servlet.http_[2.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.equinox.http.servlet_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.http_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.io.bio_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.io.nio_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server.bio_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server.handler_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server.nio_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server.session_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.server.ssl_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.949
!MESSAGE Missing imported package org.eclipse.jetty.servlet_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package org.eclipse.jetty.util_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package org.eclipse.jetty.util.component_[8.0.0,9.0.0).
!SUBENTRY 2 org.eclipse.equinox.http.jetty 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package org.eclipse.jetty.util.log_[8.0.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.950
!MESSAGE Bundle org.eclipse.equinox.http.registry_1.1.200.v20120522-2049 [92] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.http.registry 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet_2.3.0.
!SUBENTRY 2 org.eclipse.equinox.http.registry 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet.http_2.3.0.
!SUBENTRY 2 org.eclipse.equinox.http.registry 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.950
!MESSAGE Bundle org.eclipse.equinox.http.servlet_1.1.300.v20120522-1841 [93] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet_[2.3.0,3.1.0).
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing optionally imported package javax.servlet.annotation_2.6.0.
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing optionally imported package javax.servlet.descriptor_2.6.0.
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet.http_[2.3.0,3.1.0).
!SUBENTRY 2 org.eclipse.equinox.http.servlet 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.950
!MESSAGE Bundle org.eclipse.equinox.jsp.jasper_1.0.400.v20120522-2049 [94] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet_[2.4.0,3.1.0).
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing optionally imported package javax.servlet.annotation_2.6.0.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing optionally imported package javax.servlet.descriptor_2.6.0.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet.http_[2.4.0,3.1.0).
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet.jsp_[2.0.0,2.3.0).
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package org.apache.jasper.servlet_[0.0.0,6.0.0).
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.950
!MESSAGE Bundle org.eclipse.equinox.jsp.jasper.registry_1.0.300.v20120522-2049 [95] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper.registry 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package org.eclipse.equinox.jsp.jasper_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper.registry 2 0 2012-09-13 17:29:06.950
!MESSAGE Missing imported package javax.servlet_2.4.0.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper.registry 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet.http_2.4.0.
!SUBENTRY 2 org.eclipse.equinox.jsp.jasper.registry 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(|(&(osgi.ee=CDC/Foundation)(version=1.0))(&(osgi.ee=JavaSE)(version=1.3)))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.help.webapp_3.6.100.v20120521-2344 [135] was not resolved.
!SUBENTRY 2 org.eclipse.help.webapp 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required bundle org.eclipse.equinox.jsp.jasper.registry_1.0.100.
!SUBENTRY 2 org.eclipse.help.webapp 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required bundle org.eclipse.equinox.http.registry_1.0.200.
!SUBENTRY 2 org.eclipse.help.webapp 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet_2.4.0.
!SUBENTRY 2 org.eclipse.help.webapp 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet.http_2.4.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.jdt.apt.pluggable.core_1.0.400.v20120522-1651 [139] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.tool_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.dispatch_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.model_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.util_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.jdt.compiler.apt_1.0.500.v20120522-1651 [141] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.compiler.apt 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing optionally imported package org.eclipse.jdt.internal.compiler.tool_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.compiler.apt 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.jdt.compiler.tool_1.0.101.v20120522-1651 [142] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.compiler.tool 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing required capability Require-Capability: osgi.ee; filter="(&(osgi.ee=JavaSE)(version=1.6))".
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.jetty.continuation_8.1.3.v20120522 [155] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.continuation 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.continuation 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing optionally imported package org.mortbay.log_[6.1.0,7.0.0).
!SUBENTRY 2 org.eclipse.jetty.continuation 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing optionally imported package org.mortbay.util.ajax_[6.1.0,7.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.951
!MESSAGE Bundle org.eclipse.jetty.http_8.1.3.v20120522 [156] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.io_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.io.bio_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.util_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.util.component_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.util.log_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.util.resource_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.http 2 0 2012-09-13 17:29:06.951
!MESSAGE Missing imported package org.eclipse.jetty.util.ssl_[8.1.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.952
!MESSAGE Bundle org.eclipse.jetty.io_8.1.3.v20120522 [157] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.io 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.io 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.component_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.io 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.log_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.io 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.thread_[8.1.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.952
!MESSAGE Bundle org.eclipse.jetty.security_8.1.3.v20120522 [158] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.http_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.server_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.server.handler_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.component_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.log_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.resource_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.security 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.util.security_[8.1.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.952
!MESSAGE Bundle org.eclipse.jetty.server_8.1.3.v20120522 [159] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package javax.servlet.descriptor_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.continuation_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.http_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.http.gzip_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.io_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.952
!MESSAGE Missing imported package org.eclipse.jetty.io.bio_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.io.nio_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.jmx_8.0.0.
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.component_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.log_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.resource_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.ssl_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.statistic_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.server 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.thread_[8.1.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.953
!MESSAGE Bundle org.eclipse.jetty.servlet_8.1.3.v20120522 [160] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package javax.servlet.descriptor_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.continuation_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.http_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.io_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.jmx_8.0.0.
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.security_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.server_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.server.handler_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.server.nio_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.server.session_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package org.eclipse.jetty.server.ssl_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.component_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.log_[8.1.0,9.0.0).
!SUBENTRY 2 org.eclipse.jetty.servlet 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.eclipse.jetty.util.resource_[8.1.0,9.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2012-09-13 17:29:06.953
!MESSAGE Bundle org.eclipse.jetty.util_8.1.3.v20120522 [161] was not resolved.
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package javax.servlet_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing imported package javax.servlet.http_2.6.0.
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.slf4j_[1.5.0,2.0.0).
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.953
!MESSAGE Missing optionally imported package org.slf4j.helpers_[1.6.0,2.0.0).
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.954
!MESSAGE Missing optionally imported package org.slf4j.impl_[1.5.0,2.0.0).
!SUBENTRY 2 org.eclipse.jetty.util 2 0 2012-09-13 17:29:06.954
!MESSAGE Missing optionally imported package org.slf4j.spi_[1.6.0,2.0.0).

!ENTRY org.eclipse.osgi 4 0 2012-09-13 17:29:06.954
!MESSAGE Application error
!STACK 1
java.lang.ArrayIndexOutOfBoundsException: 0
   at org.eclipse.e4.core.internal.di.ConstructorRequestor.calcDependentObjects(ConstructorRequestor.java:79)
   at org.eclipse.e4.core.internal.di.Requestor.getDependentObjects(Requestor.java:135)
   at org.eclipse.e4.core.internal.di.InjectorImpl.resolveArgs(InjectorImpl.java:406)
   at org.eclipse.e4.core.internal.di.InjectorImpl.internalMake(InjectorImpl.java:311)
   at org.eclipse.e4.core.internal.di.InjectorImpl.make(InjectorImpl.java:240)
   at org.eclipse.e4.core.contexts.ContextInjectionFactory.make(ContextInjectionFactory.java:161)
   at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createDefaultHeadlessContext(E4Application.java:420)
   at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createDefaultContext(E4Application.java:434)
   at org.eclipse.e4.ui.internal.workbench.swt.E4Application.createE4Workbench(E4Application.java:182)
   at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:554)
   at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:540)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:124)
   at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
   at java.lang.reflect.Method.invoke(libgcj.so.10)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1414)
```

---

### Post by lucacerone on 2012-09-15
I am having the same errors after the latest updates..
whenever I launch eclipse (CDT) I receive a lot of runtime errors..

---

### Post by lucacerone on 2012-09-15
Ok I could find a solution (askubuntu and other forums):
1. close eclipse
2. open a terminal (CTRL+ALT+T)
3. type:```
sudo apt-get --reinstall install tzdata-java
```

After that everything works fine on my computer :)

---

### Post by jaithehulk on 2012-09-16
Thanks this really helped me...

---

### Post by lucacerone on 2012-09-16
It was a pleasure!

When you can, can you mark the thread as solved?

---

