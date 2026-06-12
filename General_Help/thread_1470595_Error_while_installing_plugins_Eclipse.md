---
title: "Error while installing plugins Eclipse"
date: 2010-05-03
forum: General Help
---

### Post by JorgeM93 on 2010-05-03
Hi folks

I would like to start programming games in Linux via python-pygame. I like Eclipse a lot, and it would be great to use it to code in python through the PyDev plugin, but, I don't know why, Eclpse doesn't let me install plugins, it starts downloading the files an then complains about the unsigned content of them and it finally drops the following error message

```
'Install' has encountered a problem:
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.pde 3.4.100.v201002111343, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  Cannot connect to keystore.
  This trust engine is read only.
  The artifact file for osgi.bundle,org.eclipse.pde,3.4.100.v201002111343 was not found.
```I tried to install another plugin (Mylyn), just for testing and it didn't work either.

I would appreciate your help

Thank you

PS: Below my signature says "Karmic Koala", but I'm currently using a fresh install of Lucid Lynx. I will update it then.

---

### Post by JorgeM93 on 2010-05-12
bump

---

### Post by KRopa on 2010-05-16
Hello, JorgeM93, I had the same problem after a fresh Lucid install and trying to add the "PDT" plug-in.

I found a solution which worked for me in FauZt's May 6th reply here:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/569224](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/569224)

After going into Synaptic and adding the "eclipse" and "eclipse-pde" packages, I was able to install the plug-in AOK.

---

### Post by JorgeM93 on 2010-05-17
Thank you!

Installing the 'eclipse' and 'eclipse-pde' packages solved it

---

### Post by gksmithlcw on 2010-07-18
Thanks, indeed! This solved my problem getting the ADT plugin installed too. :)

---

### Post by arubislander on 2010-09-12
Mine also. Many Thanks

---

### Post by Grimmy on 2010-12-13
I had this issue trying to install the Android ADT in Eclipse 3.5.2 on Ubuntu 10.04 (64bit) - Installing eclipse-pde fixed it for me. Thanks!

---

