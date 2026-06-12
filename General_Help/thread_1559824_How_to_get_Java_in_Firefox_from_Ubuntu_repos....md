---
title: "How to get Java in Firefox from Ubuntu repos..."
date: 2010-08-24
forum: General Help
---

### Post by emanuel.b on 2010-08-24
I'd like to know if there's an easy way to get Java installed in Firefox, without having to download from Java.com and installing manually.

---

### Post by surfer on 2010-08-24
there is a free version of the java runtime as firefox plugin:
```
s sudo apt-get install icedtea6-plugin
```
(this is for lucid).

---

### Post by emanuel.b on 2010-08-24
Thanks, that works just fine.

---

### Post by garvinrick4 on 2010-08-24
**3. Java**

 Ubuntu 10.04 uses OpenJDK, which mostly derives from Sun's JRE, as its  default flavor of JRE. Moreover Icddtea is the default browser plugin to  run Java applets. Most users should be fine with those JRE versions. If  you don't have them installed simply type:  ```
sudo apt-get install openjdk-6-jre icedtea6-plugin
``` However you can still install Sun's JRE and JDK like this if you are not  satisfied with those packages. To do so first you must enable the  partner repository. Go to System > Administration > Synaptic  Package Manager > Settings > Repositories > Other Software and  enable the partner repository. Now you can either search for  sun-java6-jre, sun-java6-plugin, sun-java6-jdk using Synaptic or type  the following commands in a terminal. **Sun Java Runtime Environment (JRE) and Firefox Java Plugin**

 Close Firefox if it's running, open a terminal and type:
 
 ```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

[http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide](http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide)

---

