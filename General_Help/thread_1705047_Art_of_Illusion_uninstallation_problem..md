---
title: "Art of Illusion uninstallation problem."
date: 2011-03-11
forum: General Help
---

### Post by Bcrowes11 on 2011-03-11
I was just curious about dreadful animation program Art of Illusion, so I installed it. The problem is I can't figure out how to uninstall it. I extracted the jar file labeled uninstaller and it gave me some files that look like extra crud and they look like they can't uninstall anything. If anyone knows how to help me please do...

---

### Post by uRock on 2011-03-11
Does the program show up when searching the Ubuntu Software Center or Synaptic Package Manager?

---

### Post by Bcrowes11 on 2011-03-11
No, not that I can find. I searched in the synaptic package manager, and software center.

---

### Post by TeoBigusGeekus on 2011-03-11
Perhaps it wasn't an archive, but a java executable.
Try
```
chmod +x nameofuninstaller.jar
```
to make it executable and then
```
sudo java -jar nameofuninstaller.jar
```
to execute it.

---

### Post by Bcrowes11 on 2011-03-11
Ok, let's see...Inside the Uninstaller folder that was extracted from the uninstaller.jar file there are a 

com folder, img folder, META-INF folder, net folder, a file named executables, install.log file, jarlocation.log file, langpack.xml file, rootscript file, uninstaller Jars file, uninstallerListeners file...

I tried the executable file, it just opens in the browser and keeps saying save or open? and I just pick cancel.

---

### Post by TeoBigusGeekus on 2011-03-11
> **Bcrowes11 said:**
> Ok, let's see...Inside the Uninstaller folder that was extracted from the uninstaller.jar file there are a 

com folder, img folder, META-INF folder, net folder, a file named executables, install.log file, jarlocation.log file, langpack.xml file, rootscript file, uninstaller Jars file, uninstallerListeners file...

I tried the executable file, it just opens in the browser and keeps saying save or open? and I just pick cancel.

Sorry, I edited my post after you read it.
Bumping now for you to see the edited one.

---

### Post by Bcrowes11 on 2011-03-11
When I do that comman you said it says unable to access jarfile uninstaller.jar

---

### Post by TeoBigusGeekus on 2011-03-11
First navigate to the folder where the file is.
```
cd /path/to/folder
```

---

### Post by Bcrowes11 on 2011-03-11
> **TeoBigusGeekus said:**
> First navigate to the folder where the file is.
```
cd /path/to/folder
```
It keeps on giving me 

> bash: cd: /homefolder/artofillusions/uninstaller: No such file or directory 

---

### Post by TeoBigusGeekus on 2011-03-11
It can't be "homefolder".
Try with
```
cd ~/artofillusions/uninstaller
```

---

### Post by Bcrowes11 on 2011-03-11
> **TeoBigusGeekus said:**
> It can't be "homefolder".
Try with
```
cd ~/artofillusions/uninstaller
```

I get the same bash...

---

### Post by TeoBigusGeekus on 2011-03-11
Ok, where's the jar file?

---

### Post by Bcrowes11 on 2011-03-11
In the uninstaller folder....

---

### Post by TeoBigusGeekus on 2011-03-11
> **Bcrowes11 said:**
> In the uninstaller folder....

...which is in what folder/s?

---

### Post by Bcrowes11 on 2011-03-11
> **TeoBigusGeekus said:**
> ...which is in what folder/s?
The uninstaller.jar file is in the uninstaller folder...

---

### Post by TeoBigusGeekus on 2011-03-11
Yep. Right. Could you post the whole path of the uninstaller.jar?
We're taking up precious forums' bandwidth...

---

### Post by Bcrowes11 on 2011-03-11
> "homefolder"/ArtOfIllusion/Uninstaller/Uninstaller.jar

That's where.

---

### Post by TeoBigusGeekus on 2011-03-11
```
cd ~/ArtOfIllusion/Uninstaller/
```
Does this give you an error message?

---

### Post by Bcrowes11 on 2011-03-11
No, it ads that to the command line. does that mean I can run the jar file?

---

### Post by TeoBigusGeekus on 2011-03-11
Yeah!!!!!!!!!!!!

---

### Post by Bcrowes11 on 2011-03-11
Uhh...problem....

> invalid file (bad magic number): Exec format error

---

