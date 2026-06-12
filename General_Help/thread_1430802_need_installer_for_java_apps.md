---
title: "need installer for java apps"
date: 2010-03-15
forum: General Help
---

### Post by tjk on 2010-03-15
I'm not a programmer, but I would think that it would be possible to create a linux app that would install java apps... 

Among other things the installer would: 1) request which java app is to be installed (and decompress if needed), 2) look for java installers and execute, 3) if no java installer exists the installer would create and move files to the appropriate (specified) folder, and 4) finally it would create a menu item in the Ubuntu menu.

If there is a linux app that already does this, what is it?  If this is not possible, why not?

---

### Post by luigi_mb on 2010-03-15
> **tjk said:**
> I'm not a programmer, but I would think that it would be possible to create a linux app that would install java apps... 

Among other things the installer would: 1) request which java app is to be installed (and decompress if needed), 2) look for java installers and execute, 3) if no java installer exists the installer would create and move files to the appropriate (specified) folder, and 4) finally it would create a menu item in the Ubuntu menu.

If there is a linux app that already does this, what is it?  If this is not possible, why not?

Assuming java is already properly installed in your system, installation of java applications can vary depending on how you obtained them.

If the package you downloaded is of the type archivename.tar.gz or archivename.taz, or archivename.tar.bz2, you must first unpack it. Use
one of 

```

$ tar xvf archivename.tar.gz
$ tar xvf archivename.taz
$ tar xvf archivename.tar.bz2

```

Then read the instructions (README, README.txt, INSTALL, etc.). Quite often it is sufficient to execute

```

java -jar installer.jar

```

replacing of course "installer.jar" with the appropriate .jar file in the archive.

If there is no archive, and you downloaded a .jar file, then  

```

java -jar installer.jar

```

replacing of course "installer.jar" with the appropriate .jar file in the archive.

/luigi

---

### Post by tjk on 2010-03-29
I don't see why the decisions that you have outlined below couldn't be programmed in an app... it's a basic if -> then statement to automatically determine which option would be correct...

> **luigi_mb said:**
> Assuming java is already properly installed in your system, installation of java applications can vary depending on how you obtained them.

If the package you downloaded is of the type archivename.tar.gz or archivename.taz, or archivename.tar.bz2, you must first unpack it. Use
one of 

```

$ tar xvf archivename.tar.gz
$ tar xvf archivename.taz
$ tar xvf archivename.tar.bz2

```Then read the instructions (README, README.txt, INSTALL, etc.). Quite often it is sufficient to execute

```

java -jar installer.jar

```replacing of course "installer.jar" with the appropriate .jar file in the archive.

If there is no archive, and you downloaded a .jar file, then  

```

java -jar installer.jar

```replacing of course "installer.jar" with the appropriate .jar file in the archive.

/luigi

---

