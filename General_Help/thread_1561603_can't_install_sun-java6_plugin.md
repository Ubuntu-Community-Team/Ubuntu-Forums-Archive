---
title: "can't install sun-java6 plugin"
date: 2010-08-26
forum: General Help
---

### Post by MSchlemski on 2010-08-26
I've just upgraded to Ubuntu 10.04 and am trying to install the sun java6 plugin. I've tried:

sudo apt-get install sun-java6-jre sun-java6-plugin

I got the following response:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description matched "sun-java6-plugin"
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description matched "sun-java6-plugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


I then went to the Ubuntu Software Center under Applications. I found sun java6 but there was no "install" button,as there is for the other software available. 

Am I doing something wrong? Any advice? I need the java plugin...any suggestions other than sun?

Thanks

---

### Post by arubislander on 2010-08-26
You need to enable the partner repository in System>Administration>Software Sources, the second tab, probably the first line (**[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid** partner)

---

### Post by kerry_s on 2010-08-26
you can just install "ubuntu-restricted-extras" & get most everything you need including the open java, which works just as well if not better.

---

### Post by pricetech on 2010-08-26
Also try Synaptic Package Manager, after enabling the Partner repos of course.

---

### Post by sikander3786 on 2010-08-26
> **kerry_s said:**
> you can just install "ubuntu-restricted-extras" & get most everything you need including the open java, which works just as well if not better.

+1 for ubuntu-restricted-extras.

Nearly everything restricted in one package, java, flash, codecs, fonts etc etc.

---

