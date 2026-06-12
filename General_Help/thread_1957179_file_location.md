---
title: "file location"
date: 2012-04-12
forum: General Help
---

### Post by winzip on 2012-04-12
I am looking for a property file. File name is alfresco.property.
I want to find its location.
I tried.
 whereis alfresco.property.
But it does not show any match.
Am i missing anything?

---

### Post by kiirokurisu on 2012-04-12
Try the following:
```
sudo updatedb
locate alfresco.property
```

---

### Post by winzip on 2012-04-12
> **kiirokurisu said:**
> Try the following:
```
sudo updatedb
locate alfresco.property
```

What is updatedb ? I guess i dont need that part.
Locate part should be fine. Right ?

---

### Post by kiirokurisu on 2012-04-12
updatedb update the files index - if the file you are looking for was created recently it might not show up in the locate search until you run the updatedb command.

---

### Post by Elaztic on 2012-04-12
If you are a GUI type of guy you can use your file manager and hit ctrl+h (show hidden files) and browse for it.
Im at work now from a Windows machine but as far as I remember there is both a .config and a .application library in your home dir that contains configuration files for applications....

---

### Post by winzip on 2012-04-12
> **kiirokurisu said:**
> updatedb update the files index - if the file you are looking for was created recently it might not show up in the locate search until you run the updatedb command.

Thanks.   This works.

---

