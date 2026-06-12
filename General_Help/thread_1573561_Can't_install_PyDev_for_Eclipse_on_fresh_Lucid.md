---
title: "Can't install PyDev for Eclipse on fresh Lucid"
date: 2010-09-12
forum: General Help
---

### Post by narnie on 2010-09-12
Hello,

I am having trouble installing PyDev using Eclipse. I have even downloaded the zip and installed it in /usr/share/eclipse. I've put it in my ~/.eclipse. I've deleted my ~/.eclipse. Made sure all had rwxr-xr-x for all paths where it was installed (by both Eclipse and me). PyDev never shows up under Menu->Window->Preferences.

I get this windowed error:

```
'Install' has encountered a problem:
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.pde 3.4.100.v201002111343, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  Cannot connect to keystore.
  This trust engine is read only.
  The artifact file for osgi.bundle,org.eclipse.pde,3.4.100.v201002111343 was not found.
```

This is similar in report of [http://ubuntuforums.org/newthread.php?do=postthread&f=331]("http://ubuntuforums.org/newthread.php?do=postthread&f=331")
However, those affected had resolution when eclipse-pde was installed. This is now a dependence of eclipse, so it was already installed on my system. Can anyone please lead me in the right direction?

Thanksfully,
Narnie

---

### Post by narnie on 2010-09-12
Correction, just figured out that I can install PyDev separately, but not the Django template editors.

Since I was getting ready to dive into Django, this is disappointing. I have PyDev installed, and I'm pleased with that, but would like to get Django going, too.

Any idea?

Cheerio,
Narnie

---

