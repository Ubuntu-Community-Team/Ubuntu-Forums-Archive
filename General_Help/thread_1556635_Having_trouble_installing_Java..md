---
title: "Having trouble installing Java."
date: 2010-08-19
forum: General Help
---

### Post by Artemis Fowl on 2010-08-19
I need Java in order to play Minecraft - something I cannot live without - but the Java's install intstructions are complicated and the commands error, as do all of the google results. Can someone help me?

EDIT: If you don't know, Minecraft runs in what (I think) is called an applet, so I think I would also need a plugin for firefox.

---

### Post by howefield on 2010-08-19
Enable the partner repository in you Software Sources.

System > Administration > Software Sources > Other Software Tab.

Then open Synaptic Package Manager and install the following 3 packages.

sun-java6-jre sun-jave6-plugins sun-java6-fonts

---

### Post by Artemis Fowl on 2010-08-19
What do you mean by "Enable partner repository"?

---

### Post by Artemis Fowl on 2010-08-19
Please help.

---

### Post by Zirts on 2010-08-19
Open up your Terminal and type:
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

---

### Post by Artemis Fowl on 2010-08-19
@ Zirts
E: Couldn't find package java

---

### Post by Zirts on 2010-08-19
Sorry, mistyped a bit, updated the code box, type it and it will install all you probably need.

```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

Restart your browser after the installation process.

If you have a powerfull machine with like 900MB-4000MB RAM you could try IceTea too wich work with FireFox and now with Google Chrome too.

---

### Post by Artemis Fowl on 2010-08-19
sudo aptitude install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description matched "sun-java6-plugin"
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description matched "sun-java6-plugin"
The following packages will be REMOVED:
  linux-headers-2.6.32-21{u} linux-headers-2.6.32-21-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 85.2MB will be freed.
Do you want to continue? [Y/n/?] 


"0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded"

Removing two but not installing any?

---

### Post by Artemis Fowl on 2010-08-19
I really need help. I'm sorry for being such a newbie at this.

---

### Post by Artemis Fowl on 2010-08-19
Again, PLEASE help! I really need Java! :mad:

---

### Post by leclerc65 on 2010-08-19
Go to
 System/Synaptic package manager/Settings/Repositories/Other Software
 Check mark the first line (Lucid partner)
 Click Reload
 In the search field type "sun java"
 Find "sun-java6-rje" , and check mark it - Ubuntu will propose few more packages, just accept them all.

---

