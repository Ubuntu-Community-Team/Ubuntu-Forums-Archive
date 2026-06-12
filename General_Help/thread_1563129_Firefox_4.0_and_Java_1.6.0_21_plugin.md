---
title: "Firefox 4.0 and Java 1.6.0_21 plugin"
date: 2010-08-28
forum: General Help
---

### Post by DrStrom on 2010-08-28
hi.

i dont get the java plugin 1.6.0_21 working in Firefox 4.0b5pre i deleted icedtea with the synaptic package manager and then I installed java 1.6.0_21 with chmod a+x and ./ .Everything goes well so far without any fault message. Then I created a symlink with ln -s ...but here i get no message ...so i dont know if everything wents well.

After i checked the java plugin in firefox and there was nothing I checked with java -version if java is there and there was no java installed. What did I wrong ?

---

### Post by lovinglinux on 2010-08-28
I just installed via Synpatic and didn't perform any additional modifications and is working here. I have tested the Adobe version and IcedTea.

Test it at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by lovinglinux on 2010-08-28
BTW, if Firefox cannot recognize it (nothing shows up in a**bout[noparse]:[/noparse]plugins**) , even with java properly installed from Synpatic, then close Firefox and delete the file **pluginreg.dat** from your Firefox user profile, then start it again.

---

