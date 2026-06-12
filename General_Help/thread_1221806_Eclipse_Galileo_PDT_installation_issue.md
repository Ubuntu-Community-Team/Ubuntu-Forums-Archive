---
title: "Eclipse Galileo PDT installation issue ?"
date: 2009-07-24
forum: General Help
---

### Post by chngr on 2009-07-24
Hi,

I  installed Eclipse for Java Developers from tar.gz package, everything went well. I wanted to install PDT on to Eclipse for PHP development so that clicked help > add new software. What I see is "There is no site selected" so I can't install PDT or anything at all. There is no site in Available Software Sites section.

What should I do ?

---

### Post by nikhilk on 2009-07-24
> **chngr said:**
> Hi,

I  installed Eclipse for Java Developers from tar.gz package, everything went well. I wanted to install PDT on to Eclipse for PHP development so that clicked help > add new software. What I see is "There is no site selected" so I can't install PDT or anything at all. There is no site in Available Software Sites section.

What should I do ?

[Here]("http://help.eclipse.org/stable/index.jsp?topic=/org.eclipse.platform.doc.user/tasks/tasks-128.htm") are some instructions on the same from the official Eclipse documentation. Let us know it that does not help.

---

### Post by haruX on 2009-07-24
hi,

I believe there is a drop down list after you click add new software. If i am not mistaken, look under Galileo Releases or something similar.

---

### Post by chngr on 2009-07-24
Thank you for the quick response. 

Thanks nikhilk, I know how to add software sites, what I dont know is PDT's url for Galileo.

Yes, haruX there is a dropdown list, the problem is that there is no update or software sites available in that list. I mean that dropdown list is completely empty :) I don't know this is a bug or not but this eclipse thing is getting very annoying and always problematic.

---

### Post by chngr on 2009-07-24
Eclipse + Linux, They ruined my life :D Because Eclipse runs far more slower than on Windows, I don't know why.
And That's the solution; rm -rf eclipse .... install Netbeans on windows.

---

### Post by tute666 on 2009-07-27
> **chngr said:**
> Eclipse + Linux, They ruined my life :D Because Eclipse runs far more slower than on Windows, I don't know why.
And That's the solution; rm -rf eclipse .... install Netbeans on windows.

change the jvm. the default jvm works horribly with eclipse.

---

### Post by fballem on 2009-07-28
> **chngr said:**
> Thank you for the quick response. 

Thanks nikhilk, I know how to add software sites, what I dont know is PDT's url for Galileo.

Yes, haruX there is a dropdown list, the problem is that there is no update or software sites available in that list. I mean that dropdown list is completely empty :) I don't know this is a bug or not but this eclipse thing is getting very annoying and always problematic.

Don't know if you are still having the problem, but if you are then the following is the complete set of instructions on how I have installed Eclipse 3.5:

This is a general purpose IDE used for development. The current version is 3.5 (Galileo). This must be installed directly from the website ([http://www.eclipse.org](http://www.eclipse.org)), since the version of eclipse in the repositories is not current.

**Overview**

When this installation is complete:
[LIST=1]
[*]The eclipse program files will be installed in the /opt/eclipse folder.

[*]A user group called 'eclipse' will exist and authorized users will be associated with that group.

[*]All entries in the /opt/eclipse folder will: be owned by root, be associated with the eclipse group.

[*]The eclipse group will have full access to the entries in the folder. Other users will have read access.

[*]There will be a launch item in Applications > Programming that will start eclipse.

[*]The update sites: ```
http://download.eclipse.org/releases/galileo/
``` and ```
http://download.eclipse.org/technology/epp/packages/galileo/
``` will be added to the Available Software sites in the eclipse installation. The second site will allow for the installation of complete packages, such as the Rich Client Platform package.
[/LIST]

**Installation Instructions**

[LIST=1]
[*]Verify that any previous installation has been completely removed. In particular, the following needs to be verified:

[LIST=2]
[*]There is no eclipse folder under /opt. If there is, it must be deleted. sudo access will be required to delete the folder.
[*]There is no eclipse folder under /usr/local/share. If there is, it must be deleted. sudo access will be required to delete the folder.
[*]There is no entry for eclipse in either /usr/bin or /usr/local/bin. If there is, then the entry must be deleted. sudo access will be required to delete the entries.
[*]There is no entry for eclipse.desktop in /usr/share/applications. If there is, then the entry must be deleted. sudo access will be required to delete the entries.
[*]There is no configuration files for eclipse in the users' home folders. These are hidden directories. If there are any, these must be deleted.
[/LIST]

[*]Verify that there is a group called 'eclipse' and that users are authorized in that group:

[LIST=2]
[*]Select System > Administration > Users and Groups.
[*]Select Unlock and provide your password.
[*]Select Manage Groups
[*]Scroll the list to determine if there is a group called 'eclipse'. If there is not, then add the group.
[*]Ensure that all users, including root, are members of the eclipse group. This is done by ensuring that the checkbox is checked beside each user.
[/LIST]

[*]Obtain the appropriate file from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/). Only one of the packages is required. The file should be **saved to the Desktop**. I download the Eclipse Classic for 64-bit Linux.

[*]When the download has been completed, open a Terminal setup Eclipse. The following is a summary of what the commands do:

[LIST=2]
[*]The first three commands will unpack the downloaded file and move them to the /opt folder. Note that in the second command, the name of the actual file that you downloaded must be used.
[*]The next three commands will setup the ownership and permissions for the eclipse folder. The owner will be root and the group will be the eclipse group.
[*]The last two commands will make the /opt/eclipse/eclipse file executable.
[/LIST]

```

cd ~/Desktop
tar xzf eclipse-SDK-3.5-linux-gtk-x86_64.tar.gz
sudo mv eclipse /opt/eclipse
cd /opt
sudo chown -R root:eclipse eclipse
sudo chmod -R 775 eclipse
cd /opt/eclipse
sudo chmod +x eclipse
```

[*]Create a menu item. This is done by right-clicking on the menu on the top panel and adding the item. Note that the command is /opt/eclipse/eclipse. The icon can be found in the /opt/eclipse folder.

[*]Start eclipse.

[*]Use Window > Preferences > Install/Update > Available Software Sites to add the following - note that each of these is the URL to a specific site. In some cases, the first site is already on the list, in which case, it should not be duplicated:

```
http://download.eclipse.org/releases/galileo/
http://download.eclipse.org/technology/epp/packages/galileo/

```

[*]The EPP update site will allow for the installation at the package level, and may be used to install complete packages, such as the RCP plugins.
[/LIST]

From this point forward, eclipse may be run from the Application menu.

---

### Post by tafsen on 2009-07-30
Thank you for this guide :)
Is this a safe way to install Eclipse?

---

### Post by tafsen on 2009-07-30
Well the install went ok, but I can't install any updates. I just get a bunch of errors. 

eclipse.buildId=I20090611-1540
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=nb_NO
Command-line arguments:  -os linux -ws gtk -arch x86

Created Time: 2009-07-31 00:32:33.400


Error
Fri Jul 31 00:41:28 GMT+02:00 2009
Cannot connect to keystore.

java.io.IOException: JKS
at org.eclipse.osgi.internal.service.security.KeyStoreTrustEngine.findTrustAnchor(KeyStoreTrustEngine.java:144)
at org.eclipse.equinox.internal.provisional.p2.engine.CertificateChecker.checkCertificates(CertificateChecker.java:68)
at org.eclipse.equinox.internal.provisional.p2.engine.CertificateChecker.start(CertificateChecker.java:39)
at org.eclipse.equinox.internal.provisional.p2.engine.phases.CheckTrust.completePhase(CheckTrust.java:43)
at org.eclipse.equinox.internal.provisional.p2.engine.Phase.postPerform(Phase.java:195)
at org.eclipse.equinox.internal.provisional.p2.engine.Phase.perform(Phase.java:78)
at org.eclipse.equinox.internal.provisional.p2.engine.PhaseSet.perform(PhaseSet.java:44)
at org.eclipse.equinox.internal.provisional.p2.engine.Engine.perform(Engine.java:54)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProvisioningUtil.performProvisioningPlan(ProvisioningUtil.java:389)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProfileModificationOperation.doExecute(ProfileModificationOperation.java:61)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProvisioningOperation.execute(ProvisioningOperation.java:37)
at org.eclipse.equinox.internal.provisional.p2.ui.ProvisioningOperationRunner$1.run(ProvisioningOperationRunner.java:94)
at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)



Error
Fri Jul 31 00:41:28 GMT+02:00 2009
An error occurred during the org.eclipse.equinox.internal.provisional.p2.engine.phases.CheckTrust phase.

---

### Post by vpraveen84 on 2009-11-10
I think its a problem with the jdk. Try using Sun jdk, instead of gcj.

> **tafsen said:**
> Well the install went ok, but I can't install any updates. I just get a bunch of errors. 

eclipse.buildId=I20090611-1540
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=nb_NO
Command-line arguments:  -os linux -ws gtk -arch x86

Created Time: 2009-07-31 00:32:33.400


Error
Fri Jul 31 00:41:28 GMT+02:00 2009
Cannot connect to keystore.

java.io.IOException: JKS
at org.eclipse.osgi.internal.service.security.KeyStoreTrustEngine.findTrustAnchor(KeyStoreTrustEngine.java:144)
at org.eclipse.equinox.internal.provisional.p2.engine.CertificateChecker.checkCertificates(CertificateChecker.java:68)
at org.eclipse.equinox.internal.provisional.p2.engine.CertificateChecker.start(CertificateChecker.java:39)
at org.eclipse.equinox.internal.provisional.p2.engine.phases.CheckTrust.completePhase(CheckTrust.java:43)
at org.eclipse.equinox.internal.provisional.p2.engine.Phase.postPerform(Phase.java:195)
at org.eclipse.equinox.internal.provisional.p2.engine.Phase.perform(Phase.java:78)
at org.eclipse.equinox.internal.provisional.p2.engine.PhaseSet.perform(PhaseSet.java:44)
at org.eclipse.equinox.internal.provisional.p2.engine.Engine.perform(Engine.java:54)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProvisioningUtil.performProvisioningPlan(ProvisioningUtil.java:389)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProfileModificationOperation.doExecute(ProfileModificationOperation.java:61)
at org.eclipse.equinox.internal.provisional.p2.ui.operations.ProvisioningOperation.execute(ProvisioningOperation.java:37)
at org.eclipse.equinox.internal.provisional.p2.ui.ProvisioningOperationRunner$1.run(ProvisioningOperationRunner.java:94)
at org.eclipse.core.internal.jobs.Worker.run(Worker.java:55)



Error
Fri Jul 31 00:41:28 GMT+02:00 2009
An error occurred during the org.eclipse.equinox.internal.provisional.p2.engine.phases.CheckTrust phase.

---

