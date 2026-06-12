---
title: "Error while installing on hardy 8.0.4"
date: 2009-06-29
forum: General Help
---

### Post by dejavu2177 on 2009-06-29
I upgraded from gutsy to hardy a few days back and I am seeing some errors while installing Documentum. I feel this issue is related to hardy packages and not with the Documentum installer because I am seeing this only after the upgrade to hardy and all was working fine with gutsy. 
The installer has a JRE 1.5.0_12 bundled with it and I have SUN 1.5.0_16 installed. Any help would be great. Here is the error:
----------------
(Jun 27, 2009 6:59:24 PM), Setup.product.install, com.ibm.wizard.platform.linux.LinuxJVMServiceImpl, dbg.jvm, calculating size from directory /tmp/wptemp/istemp13611178195827/_bundledJRE_
(Jun 27, 2009 6:59:25 PM), Setup.product.install, com.installshield.product.service.product.PureJavaProductServiceImpl$DiskSpaceC
heck, wrn, Checking required disk space requires file service native support.
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.product.actions.UninstallerJVMResolution, dbg.jvm, attempting to use the current JVM
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.product.actions.UninstallerJVMResolution, dbg.jvm, copying the current JVM
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.ibm.wizard.platform.linux.LinuxJVMServiceImpl, dbg.jvm, copying directory /tmp/wptemp/istemp13611178195827/_bundledJRE_ to /bin/
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.product.actions.UninstallerJVMResolution, wrn, An error occurred attempting to copy the current JVM: ServiceException: (error code = 315; message = "could not create directory /bin/jre"; severity = 0)
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.product.actions.UninstallerJVMResolution, dbg.jvm, searching for a JVM
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.product.service.product.PureJavaProductServiceImpl$Installer, err, ProductException: (error code = 601; message="JVM not found")
ProductException: (error code = 601; message="JVM not found")
at com.installshield.product.actions.JVMResolution.install(Unknown Source)
at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallPro
duct.checkUninstallerJVMResolution(Unknown Source)
at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallPro
duct.install(Unknown Source)
at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.
execute(Unknown Source)
at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
at java.lang.Thread.run(Thread.java:595)
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.wizardx.conditions.PlatformWizardBeanCondition, dbg.platform, target platform: name="Linux" version="2.6.24-24-generic" arch="i386"
(Jun 27, 2009 6:59:26 PM), Setup.product.install, com.installshield.wizardx.conditions.PlatformWizardBeanCondition, dbg.platform, condition platform: name="Windows .*" version="." arch="."

---

