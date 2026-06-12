---
title: "Extract the eclipse download"
date: 2012-01-17
forum: General Help
---

### Post by 333ameeth on 2012-01-17
i am trying to Extract the eclipse download which is at  "/tmp" with the name "eclipse-java-indigo-SR1-linux-gtk.tar.gz" 
i have typed the command as "tar xf eclipse-java-indigo-SR1-linux-gtk.tar.gz" but got the [COLOR=Blue]error as : 
tar: eclipse-java-indigo-SR1-linux-gtk.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
[/COLOR]
i am new on ubuntu please tell me how to overcome this error and start the eclipse .
for information i am using ubuntu 8.10 .

---

### Post by TeoBigusGeekus on 2012-01-17
Where you in the /tmp folder when you issued the command?
If not, try with
```
tar xvf /tmp/eclipse-java-indigo-SR1-linux-gtk.tar.gz -C ~/Desktop
```
This will extract the archive on your desktop.

---

