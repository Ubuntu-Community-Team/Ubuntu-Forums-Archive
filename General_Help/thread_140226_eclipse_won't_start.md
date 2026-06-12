---
title: "eclipse won't start"
date: 2006-03-05
forum: General Help
---

### Post by majik279 on 2006-03-05
I've been playing around on and off for weeks on this. The enclosed file is my error log that I get when trying to start eclipse. I installed java using the instructions from here: [http://www.ubuntuforums.org/showthread.php?t=70428&highlight=eclipse+install](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=eclipse+install)

If someone can just tell me whether or not this is an eclipse, java, or ubuntu problem then that would be great (and maybe even direct me to the appropriate forum)

Also, sorry to be a pain, but I couldn't figure out how to just have a link to a file. It uploaded, but then I didn't see anything pointing to it.


!SESSION 2006-03-05 19:05:06.34 ------------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.update.configurator 2006-03-05 19:05:08.166
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.update.configurator 2006-03-05 19:05:08.167
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2006-03-05 19:05:08.728
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   ...18 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
Root exception:
java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(java.lang.String) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)

!ENTRY org.eclipse.osgi 2006-03-05 19:05:09.31
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)

!ENTRY org.eclipse.osgi 2006-03-05 19:05:09.275
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (Unknown Source)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (Unknown Source)

!ENTRY org.eclipse.osgi 2006-03-05 19:05:09.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar[/email] [23] was not resolved.

---

