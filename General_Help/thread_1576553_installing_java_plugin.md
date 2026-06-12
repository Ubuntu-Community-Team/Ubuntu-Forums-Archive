---
title: "installing java plugin"
date: 2010-09-17
forum: General Help
---

### Post by pungwe on 2010-09-17
cannot install java plugin
tried from within the browser and  got  an error
tried  with apt-get

sudo apt-get install openjdk-6-jre icedtea6-plugin

got the following 

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main xulrunner-1.9.2 1.9.2.8+build1+nobinonly-0ubuntu0.9.10.1
  404  Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main xulrunner-1.9.2 1.9.2.8+build1+nobinonly-0ubuntu0.9.10.1
  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.8+build1+nobinonly-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.8+build1+nobinonly-0ubuntu0.9.10.1_i386.deb)  404  Not Found [IP: 91.189.92.167 80]

not exactly what I need at this point.

---

### Post by TBABill on 2010-09-17
Depending on whether you want Sun Java or Open Java, go into synaptic and search "java", find the version you want, right click, select for installation, click apply....wait for the install to finish and enjoy. But don't install both. If one is installed and not working properly, uninstall it, then install the one you want.
 
Edit: If you don't have all the codecs installed, easiest to go into Ubuntu Software Center and just install Ubuntu Restricted Extras so you'll get them all including Java. If you specifically want Sun Java you will then have to uninstall open java and reinstall with sun java via synaptic. It's a pain, but it works better than the open java.

---

### Post by ajgreeny on 2010-09-17
You must also have the partner repos enabled as that is where the sun-java packages are now, and that is probably the best version of the plugin to use.

---

