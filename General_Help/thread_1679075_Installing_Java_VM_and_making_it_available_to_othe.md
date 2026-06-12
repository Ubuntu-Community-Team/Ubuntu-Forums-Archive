---
title: "Installing Java VM and making it available to other programs"
date: 2011-01-31
forum: General Help
---

### Post by hojjat on 2011-01-31
I'm trying to install a program which requires Java VM.

The installer is a install.bin file, coming with a eclipse folder; in this folder, you can find a "jre" directory.

I also installed Coconut Java virtual machine, as well as OpenJDK Java 6 runtime environment. However, I still can't install the program. Executing the installer gives me this error message:

```

Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

```

I think I should make Java VM available to the installer somehow, but I don't know how. I tried searching online but couldn't figure out the answer. Please help.

---

### Post by drewsus on 2011-01-31
You can install java by adding/enabling the Partners repo and updating your sources:
```
sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
sudo apt-get update
```

Then install java:
```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
```

Then set your system to use it:
```
sudo update-java-alternatives -s java-6-sun
```

And finally, you can install Eclipse from the repos:
```
sudo apt-get install eclipse
```

Does this help?

---

### Post by hojjat on 2011-01-31
I will try it out tomorrow. However, I don't think this whole thing is needed to be done. Correct me if I'm wrong, but since the package has eclipse and jre in it, I shouldn't really need to install them; all I really need to do is to make it understand where to find the JRE subfolder.

---

### Post by drewsus on 2011-01-31
Okay, wait. What is this install.bin file for/from?

---

### Post by hojjat on 2011-01-31
The package I'm trying to install is IBM Data Studio 2.2, and the linux version (which is originally developed for SuSE and RedHat) can be found here: [http://www.ibm.com/developerworks/downloads/im/data/](http://www.ibm.com/developerworks/downloads/im/data/)

You can download it for free if you want to (registration is free, software is also free).

The Linux downloadable is a ZIP archive; once you unzip it, there is an install.bin file, and a folder named eciplse. Inside the latter, there's a directory named jre.

---

### Post by drewsus on 2011-01-31
You must have downloaded the Stand Alone version? I ask because I downloaded the IDE version and it had "**setup**" instead of "**install.bin**". The IDE version installed fine by downloading, unzipping and running:
```
sudo ./setup
```

[img]http://i.imgur.com/Aj0k8.jpg[/img]
[img]http://i.imgur.com/vB5pk.jpg[/img]
[img]http://i.imgur.com/BDv9H.png[/img]

---

### Post by hojjat on 2011-01-31
Perfect answer!

---

