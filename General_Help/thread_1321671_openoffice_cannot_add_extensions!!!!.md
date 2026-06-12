---
title: "openoffice cannot add extensions!!!!"
date: 2009-11-10
forum: General Help
---

### Post by pythonscript on 2009-11-10
I'm using openoffice 3.0.1 write, in this case, and when I try to install an extension from Tools -> Extension Manager -> Add, I get an error window that says "Could not create Java implementation loader" and the extension isn't loaded! This happens *every time* I try to install a plugin, and I can't use openoffice if I can't use these plugins. Please help!

---

### Post by jmszr on 2009-11-10
pythonscript,

Try this:

```
sudo apt-get install openoffice.org-java-common
```

and see if the extensions will then install.

---

### Post by Hagar Delest on 2009-11-10
Make sure that there is a java version checked in Tools>Options>OOo>Java.

---

### Post by pythonscript on 2009-11-11
> **Hagar de l'Est said:**
> Make sure that there is a java version checked in Tools>Options>OOo>Java.

This works! I ran ```
sudo update-alternatives --config java
``` and saw that the openjdk was the default java environment, so I changed it to the sun-java6-jre instead and selected it in the menu you specified, and it's working flawlessly now. Thanks!

---

