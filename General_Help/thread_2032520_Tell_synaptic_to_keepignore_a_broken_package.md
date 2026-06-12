---
title: "Tell synaptic to keep/ignore a broken package ?"
date: 2012-07-24
forum: General Help
---

### Post by scotty64 on 2012-07-24
How can I stop apt/synaptic from wanting to remove a broken package everytime I start synaptic or apt ? I force-installed the package in question (simon-listens voice recognition), because it works (with libattica0.3) despite a missing dependency (libattica0) that cannot be resolved. As no other applications depend on this package I consider it safe to keep the broken installation. Yes, I am already in contact with the package maintainer, but I would like to continue to work with Simon until a fix is realeased.

---

### Post by dino99 on 2012-07-24
How to fix broken packages

IconsPage/warning.png 'Broken packages' are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow any further changes to the system until all broken packages have been fixed.

    To fix broken packages

        Choose Edit > Fix Broken Packages from the menu.

        Choose Apply Marked Changes from the Edit menu or press Ctrl + P.

        Confirm the summary of changes and click Apply. 

If that does not help, then please follow this procedure:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

