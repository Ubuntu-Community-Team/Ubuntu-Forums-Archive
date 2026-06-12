---
title: "Java Control Panel doesn't save Runtime Parameters"
date: 2009-07-17
forum: General Help
---

### Post by hontvari on 2009-07-17
I would like to enable OpenGL acceleration for Java applets. I tried to change the Runtime Parameter column in both the User and System tab of the Java Runtime Environment Settings dialog of the Java Control Panel. I can indeed change the column, but when I reopen the dialog the column is empty again.

The JRE is SUN 1.6.0 14.

---

### Post by Michal Šrajer on 2009-11-30
Workaround:
vim /home/michal/.java/deployment/deployment.properties

edit line: 
"deployment.javaws.jre.0.args="

Works for me.
Best regards,
Michal

---

