---
title: "Apt-Get blackdown 64 bit java"
date: 2004-10-20
forum: General Help
---

### Post by snowx1000 on 2004-10-20
It would be nice if this package was available and would be added to path and everything automatically, would like to get azureus working. :-)

---

### Post by shellreef on 2004-12-29
I second this. I wasn't able to get any of the following Blackdown packages to install:

blackdown-j2re1.3debian - Debian specific parts of Java(TM) 2 RE, Standard Edition
blackdown-j2re1.4debian - Debian specific parts of Java(TM) 2 RE, Standard Edition
blackdown-j2sdk1.3debian - Debian specific parts of Java(TM) 2 SDK, Standard Edition
blackdown-j2sdk1.4debian - Debian specific parts of Java(TM) 2 SDK, Standard Edition

All of them fail with a message similar to:

$ sudo apt-get install blackdown-j2re1.3debian
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  blackdown-j2re1.3debian: Depends: blackdown-j2re1.3 but it is not installable
E: Broken packages

I'd  like to get Blackdown working because it comes with a Mozilla plugin (/opt/blackdown-jdk-1.4.2.01/jre/plugin/amd64/mozilla/libjavaplugin_oji.so). The amd64 jre1.5.0_01 JRE from Sun doesn't come with a plugin/ directory, so you can't (as far as I Know) use it in Firefox.

---

