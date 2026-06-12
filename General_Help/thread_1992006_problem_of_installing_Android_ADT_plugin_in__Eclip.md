---
title: "problem of installing Android ADT plugin in  Eclipse"
date: 2012-05-31
forum: General Help
---

### Post by chaopoch on 2012-05-31
I install Android ADT plugin in  Eclipse (version 3.7.2), and I can confirm that all these 4 plugins are exactly installed by checking  Help -> About Eclipse Plateform -> Installation Details.

However, there is no "Android" option in Windows -> Preferences, any way to solve it? thanks for reply.

---

### Post by chaopoch on 2012-05-31
No one ever experienced this problem?
any clue is appreciated.

---

### Post by rraffensperger on 2012-06-22
I have the same problem.  I also have the problem with egit plugin.  Both show installed, but they don't show up in the menus.  One clue may be that I also can not update Eclipse, after downloading the update, it begins the update and then fails with the error:

An error occurred while uninstalling
session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.p2.engine.phases.Uninstall, operand=[R]org.eclipse.platform_root 3.7.2.dist-9nF7UHagFqn9pElwWhC90gLz-soEuSGYmtSeiRH --> null, action=org.eclipse.equinox.internal.p2.touchpoint.natives.actions.CleanupzipAction).
Backup of file /usr/lib/eclipse/.eclipseproduct failed.
File that was copied to backup could not be deleted: /usr/lib/eclipse/.eclipseproduct

UPDATE: Solved
Installed Eclipse from the eclipse.org site and everything works fine. Some problem with the Ubuntu package on 64-bit.

---

### Post by mrsirrisrm on 2012-08-28
I had the same problem as rraffensperger, on 12.04 64 bit. Also solved by installing Eclipse from eclipse.org

---

