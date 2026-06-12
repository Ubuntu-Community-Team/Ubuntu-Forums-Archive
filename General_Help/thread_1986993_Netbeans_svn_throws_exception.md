---
title: "Netbeans svn throws exception"
date: 2012-05-25
forum: General Help
---

### Post by Zvlwab on 2012-05-25
I installed Netbeans from the repositories. When I navigate to a project, try to open it or click on Check out, the following exception is thrown:
```
A java.lang.NoClassDefFoundError exception has occurred.
Please report this at http://www.netbeans.org/community/issues.html,
including a copy of your messages.log file as an attachment.
The messages.log file is located in your ~/.netbeans/7.0/var/log folder.
```
Details
```
java.lang.ClassNotFoundException: org.tigris.subversion.javahl.SVNClientInterface
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Caused: java.lang.ClassNotFoundException: org.tigris.subversion.javahl.SVNClientInterface starting from ModuleCL@6bc5af2e[org.netbeans.libs.svnClientAdapter] with possible defining loaders [ModuleCL@5d352367[org.netbeans.libs.svnClientAdapter.javahl], ModuleCL@6b96bac4[org.netbeans.libs.svnClientAdapter.svnkit]] and declared parents [org.netbeans.MainImpl$BootClassLoader@35a8767]
	at org.netbeans.ProxyClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Caused: java.lang.NoClassDefFoundError: org/tigris/subversion/javahl/SVNClientInterface
	at org.netbeans.libs.svnclientadapter.javahl.JavaHlClientAdapterFactory.isAvailable(Unknown Source)
	at org.netbeans.libs.svnclientadapter.SvnClientAdapterFactory.getInstance(Unknown Source)
	at org.netbeans.modules.subversion.client.SvnClientFactory.setupJavaHl(Unknown Source)
	at org.netbeans.modules.subversion.client.SvnClientFactory.setup(Unknown Source)
	at org.netbeans.modules.subversion.client.SvnClientFactory.init(Unknown Source)
	at org.netbeans.modules.subversion.client.SvnClientFactory.getInstance(Unknown Source)
	at org.netbeans.modules.subversion.Subversion.getClient(Unknown Source)
	at org.netbeans.modules.subversion.util.SvnUtils.getRepositoryRootUrl(Unknown Source)
	at org.netbeans.modules.subversion.FilesystemHandler.getRemoteRepository(Unknown Source)
	at org.netbeans.modules.subversion.FilesystemHandler.getAttribute(Unknown Source)
	at org.netbeans.modules.versioning.FilesystemInterceptor$DelegatingInterceptor.getAttribute(Unknown Source)
	at org.netbeans.modules.versioning.FilesystemInterceptor$DelegatingInterceptor.access$000(Unknown Source)
	at org.netbeans.modules.versioning.FilesystemInterceptor.getAttribute(Unknown Source)
	at org.netbeans.modules.masterfs.ProvidedExtensionsProxy$11.run(ProvidedExtensionsProxy.java:288)
	at org.netbeans.modules.masterfs.ProvidedExtensionsProxy.runCheckCode(ProvidedExtensionsProxy.java:466)
	at org.netbeans.modules.masterfs.ProvidedExtensionsProxy.getAttribute(ProvidedExtensionsProxy.java:286)
	at org.netbeans.modules.masterfs.filebasedfs.fileobjects.BaseFileObj.getAttribute(BaseFileObj.java:462)
	at org.netbeans.modules.kenai.ui.KenaiNBProjectAnnotator.annotateIcon(KenaiNBProjectAnnotator.java:69)
	at org.netbeans.api.project.ProjectUtils$AnnotateIconProxyProjectInformation.updateIcon(Unknown Source)
	at org.netbeans.api.project.ProjectUtils$AnnotateIconProxyProjectInformation.annotatorsChanged(Unknown Source)
	at org.netbeans.api.project.ProjectUtils$AnnotateIconProxyProjectInformation.<init>(Unknown Source)
	at org.netbeans.api.project.ProjectUtils.getInformation(Unknown Source)
	at org.netbeans.modules.project.ui.ProjectChooserAccessory$1.run(ProjectChooserAccessory.java:258)
[catch] at org.openide.util.RequestProcessor$Task.run(Unknown Source)
	at org.openide.util.RequestProcessor$Processor.run(Unknown Source)

```

---

### Post by rhuerj on 2012-06-26
[FONT=Arial]Class  [/FONT]org.tigris.subversion.javahl.SVNClientInterface is missing[FONT=Arial]

See:
[http://netbeans.org/bugzilla/show_bug.cgi?id=212807](http://netbeans.org/bugzilla/show_bug.cgi?id=212807)
which is duplication of
[http://netbeans.org/bugzilla/show_bug.cgi?id=210759](http://netbeans.org/bugzilla/show_bug.cgi?id=210759)

Interesting note is on the end of 210759:

ovrabec wrote: 
[/FONT]The question is where you got and where you downloaded the NB installer from. But clearly the installation is corrupted.
[FONT=Arial]ilvidel wrote: 
My 7.0.1 installation comes from a standard Debian package, running: 
# apt-get install netbeans[/FONT]

---

