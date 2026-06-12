---
title: "running .jar files?"
date: 2010-12-24
forum: General Help
---

### Post by Pgimps on 2010-12-24
I just installed xubuntu and downloaded minecraft.jar and it says it's not marked as executable how would I make it executable?

---

### Post by noah++ on 2010-12-24
In general, it would be ```
chmod u+x minecraft.jar
``` from the command line. The equivalent operation under GNOME (perhaps it's similar in Xfce) is **Right Click -> Properties -> Permissions -> Allow executing file as program**.  But I wonder if you're just supposed to be running ```
java minecraft.jar
``` instead, or have *.jar*s associated with *java*. :confused:

---

### Post by alenis on 2010-12-24
Right-click it, choose properties, then the permissions tab, then check Execute.

---

### Post by Pgimps on 2010-12-25
> **noah++ said:**
> In general, it would be ```
chmod u+x minecraft.jar
``` from the command line. The equivalent operation under GNOME (perhaps it's similar in Xfce) is **Right Click -> Properties -> Permissions -> Allow executing file as program**.  But I wonder if you're just supposed to be running ```
java minecraft.jar
``` instead, or have *.jar*s associated with *java*. :confused:
I did both of them and for the first one I get 

chmod: cannot access `minecraft.jar': No such file or directory

and the second one is 

Exception in thread "main" java.lang.NoClassDefFoundError: minecraft/jar
Caused by: java.lang.ClassNotFoundException: minecraft.jar
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: minecraft.jar. Program will exit.

---

### Post by dudesurge on 2010-12-25
> **Pgimps said:**
> I did both of them and for the first one I get 

chmod: cannot access `minecraft.jar': No such file or directory


you have to specify the dir such as "/media/sda3/minecraft.jar" without quotes

so it'd be ```
chmod u=x /media/sda3/minecraft.jar 
```for me

---

### Post by Morbius1 on 2010-12-25
```
java -jar /full-path-to/minecraft.jar
```

---

### Post by Pgimps on 2010-12-25
> **Morbius1 said:**
> ```
java -jar /full-path-to/minecraft.jar
```

Ok so I got it to run in terminal, now how would I get it to run by double clicking it at my desktop

---

### Post by Morbius1 on 2010-12-25
I don't use Xubuntu but I do have Mint XFCE in a VirtualBox. Just right click the desktop > select "Create Launcher" and put your java line in the "Command" section.

---

### Post by dudesurge on 2010-12-26
oh i just remembered you can open the directory as root and change permissions, so```
sudo nautilus
``` then navigate to the folder> right click> properties> mark as executable, and that should do it if you can't enable it normally
or
right click> open with> java -jar <remember application association>

i hope these help, keep your status updated

---

### Post by veggen on 2010-12-27
I'm pretty sure there's no need to chmod anything. Just associate the file type with java -jar command and you're good to go.

---

### Post by buhmillion on 2010-12-27
chmod +x /pathto/minecraft.jar

---

### Post by Morbius1 on 2010-12-27
A jar "file" is an archive and not an executable entity. 

It won't do any harm to make it executable just as it wouldn't do any harm to make a simple non script text file executable.

---

