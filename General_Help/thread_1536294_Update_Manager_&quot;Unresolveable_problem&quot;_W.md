---
title: "Update Manager &quot;Unresolveable problem&quot; Warning, Help!"
date: 2010-07-22
forum: General Help
---

### Post by seanarickymurphy on 2010-07-22
I got this message after Updating Ubuntu in the Update Manager,
"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.' "

---

Any help!? Also when I open it it says your running on battery, I got 5 hours left of battery life, could that be a problem?

---

### Post by todak on 2010-07-22
Try choosing a different server for your updates and see if it helps. Sometimes the server will will have a mis-typed URL that causes the problem. You can choose a different server for your packages by going to  *System> Administration> Software Sources*. Under the *Ubuntu Software* tab there will be a drop box that has *Download from:* next to it. Click on the box and select *Other..* and you will be presented with a list of mirrors to choose from. Select one and click *Close* and the package list from that particular server will be automatically downloaded to your drive. Do that and see if it clears the error message. The battery life has no effect on package lists.

---

