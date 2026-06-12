---
title: "eclipse ide wont run?, i have jdk too?"
date: 2009-12-12
forum: General Help
---

### Post by srisar on 2009-12-12
hay how to run eclipse ide 3.5, i have sun java jdk 1.6.0.17, which i downloaded from sun's website. it was a package with netbeans 6.8. now netbeans working properly, but when i open eclipse its saying no JRE orJDK is found on your system..?!

what can i do please help me

---

### Post by spiderbatdad on 2009-12-12
[http://www.ubuntugeek.com/how-to-install-and-setup-eclipse-with-suns-java.html](http://www.ubuntugeek.com/how-to-install-and-setup-eclipse-with-suns-java.html)

---

### Post by srisar on 2009-12-12
thats right, that tutorial is done through apt-get, i already mentioned that i download the package manually from sun's website and intalled..., thats why its now impossible to open the eclipse, i have hoped there should be another way to configure the jvm????

---

### Post by john newbuntu on 2009-12-12
Make a backup of your eclipse.ini file.  Edit the original and look at the argument after -vm.  This the where eclipse is looking at for the jdk.  Modify this to the correct location of you jdk and start eclipse.

---

