---
title: "Ubuntu 9.10 with java 1.6 - How do i put 1.5 on as well?"
date: 2009-12-01
forum: General Help
---

### Post by Master_Ne0 on 2009-12-01
Hi,

I am a new to Ubuntu, though i didn't get much response in the beginner talk forum. As the title suggests i am running the Ubuntu 9.10 and i have installed java version 1.6 when i installed eclipse. I want to be able to build the Android source, though this needs java 1.5. I tried ```
sudo apt-get install sun-java5-jdk
``` though it fails saying it cannot find the package (worked with sun-java6-jdk). This question has been asked before, though the solutions mainly involve the above command that i cant get working. (also tried the synaptic package manager, which also couldn't find it).

Can anyone point me in the right direction? Thanks.

---

### Post by alex.mobigo on 2009-12-29
Master_Ne0

The 0xdroid guys give some directions in
> [http://code.google.com/p/0xdroid/wiki/Source](http://code.google.com/p/0xdroid/wiki/Source)I did try it without success. i guess we should change to jaunty repo a while, and install java5.

I am not sure you should go this way, just try it and let me know. i need to do the same as you.

---

### Post by a0u on 2009-12-29
J2SE 5.0 is currently deprecated, which is probably why it is no longer in the Ubuntu repositories.

It may be better to install Sun's last official release ([Java SE Development Kit 5.0u22]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-1.5.0_22-oth-JPR@CDS-CDS_Developer")) and point JAVA_HOME to the install directory.

---

### Post by alex.mobigo on 2009-12-29
Try this: [http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project](http://blog.enea.com/Blog/bid/32050/Ubuntu-9-10-Java-5-and-the-Android-Open-Source-Project)

---

### Post by hotplainrice on 2010-01-06
Method 1 worked after following the comment provided in the URL above.

---

