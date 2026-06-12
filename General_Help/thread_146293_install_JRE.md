---
title: "install JRE"
date: 2006-03-18
forum: General Help
---

### Post by voltage on 2006-03-18
Hi,

I have completly download the JRE from the java.sun.com (jre-1_5_0_06-linux-amd64.bin). Then I were follow the installation instruction from java.sun.com (./jre-1_5_0_06-linux-amd64.bin). So may I know how to make use of sun java ??

---

### Post by Perfect Storm on 2006-03-18
You can try this test: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
Also type **about: plugins** in your browser. (without the space between : and p)

---

### Post by voltage on 2006-03-18
I have try the "sudo update-alternatives --config java" to check default JRE in used. Unfortunedly I didn't saw any Sun JRE or JRE package name are list into it ... the default JRE is /usr/lib/jvm/java-gcj/bin/java.

---

### Post by Perfect Storm on 2006-03-18
But what version does it show on the test site?

---

### Post by akiro.yamamoto on 2006-03-18
[quote=voltage]I have try the "sudo update-alternatives --config java" to check default JRE in used. Unfortunedly I didn't saw any Sun JRE or JRE package name are list into it ... the default JRE is /usr/lib/jvm/java-gcj/bin/java.[/quote]

I think this is used when you follow the guide on the Ubuntu Wiki and you convert
the default java .bin installer to a .deb package and install using "dpkg -i".
I'm not sure the .bin installer functions the same way? :???:

When you issue the command do you get something similar to my pic?
If not, the installer may not have registered the java install with the system.
dpkg and apt-get maintain a list?! of installed packages.
That command is a part of the debian package maintenance system.

If the sun JRE is not listed and is not functioning properly...
1) Track down where the java .bin installer installed the files.
2) Uninstall / Delete them from your system.
3) Follow the guide on the wiki and convert the sun package to a .deb and install it that way.
This is probably the best bet and a cleaner solution than having an unmanaged
sofware package installed on your system.

---

