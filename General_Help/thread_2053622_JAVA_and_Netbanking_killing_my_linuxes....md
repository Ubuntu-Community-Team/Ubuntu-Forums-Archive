---
title: "JAVA and Netbanking killing my linuxes..."
date: 2012-09-05
forum: General Help
---

### Post by leandromartinez98 on 2012-09-05
I´m not sure if there is a solution to that, actually I´ve tried with different degrees of successes the many alternatives available over the internet. However, many banks in Brazil continue to use Java in their sites, and more and more the sites only work with the latest Java from Oracle. Since Ubuntu dropped any support to these, I have to keep a virtual machine with Windows only to use those sites. Now my mom is complaining that she cannot use the internet banking anymore... because she is using Hardy and the banks do not accept old Java versions anymore, but if I upgrade to Lucid I will not be able to install Oracle Java anymore (I´ve tried, believe me, but the results are unpredictable and break at every upgrade). That is, Java is killing my desktop linuxes. I hope someone develops a fully compatible alternative, or safe packages for Ubuntu.

---

### Post by QIII on 2012-09-05
Oracle has withdrawn licensing for anyone to keep Oracle in their repos.  Even Microsoft can't.  On a new Windows installation you have to install from Oracle.  Canonical did not drop support for Oracle Java.  Oracle made that decision.

(Do you really still have a Hardy machine?)

You can still install Oracle Java 7 very easily in Ubuntu and I currently have it running in Quantal, which is still in development.

Please see the Java wiki in my signature.  In the Oracle Java 7 section, under "Command line methods" there is a link called "Using webupd8.org's strikingly simple method".

If you use that method, webupd8's script in their PPA will automatically update Oracle Java 7 when you do your normal Ubuntu updates.

I wouldn't try this on Hardy and I would highly recommend installing a more recent release.

Why not install Precise, since it is the current LTS?

---

### Post by leandromartinez98 on 2012-09-05
Sorry, she is using Lucid, not Hardy. The reason I've not updated yet is because of Java, indeed - I simply do not update her machine anymore since this issue started, because on my machines, with updates, I've simply quited trying to make it work. I will try this method, although I've started to apply it and the first thing I notice is that I cannot remove the openjava from my machine, because the removal of the OpenJDK 6 triggers automatically the installation of the OpenJDK 7. I'm not sure if this will interfere on the installation of the oracle java.

I think Cannonical, even not being able provide java within the distribution, should provide a verified and supported howto for the installation. I cannot say that every method described may fail, but the simple observations that so many alternatives are available at the ubuntu help site shows that they are not infallible. I've been trying many of them with no success (before quiting).

For the records: the installation suggested above seems to have worked on my laptop. I will try on my other installations.

---

### Post by QIII on 2012-09-05
Oracle Java 7 is third party.  Third party propriety items are not included.  OpenJDK is in the repos because it is open source.

The verified methods for installing Oracle Java 7 are in the community wiki and the link to webupd8's method is in the wiki because I put it there.  That's the verified and supported how-to provided by the community.  Unfortunately, there is a lot of outdated and even completely wrong information out on the web.

You don't need to uninstall OpenJDK, although I would uninstall OpenJDK 6 and let it install OpenJDK 7 for the sake of security.  Then install Oracle Java.  They can coexist.  The webupd8 method will set Oracle Java 7 as the default and install the Oracle Java 7 browser plugin.

Edit:  if you already installed Oracle Java 7, don't install OpenJDK 7.

---

