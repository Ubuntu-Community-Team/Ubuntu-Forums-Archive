---
title: "64-bit java installation not working?"
date: 2010-10-03
forum: General Help
---

### Post by altjx on 2010-10-03
Trying to install Java for Ubuntu 10.10 beta 64-bit... Don't bash me, if you know how with 10.4, please help if you can.

I tried to get support from Sony online chat but when I load it in Google chrome, it says Missing Plugin... When I try in FireFOx, it says "Get JRE plugin"... when I click it, nothing happens. I tried downloading the Java x64 RPM and installed it using command line and its still telling me the same thing...

---

### Post by andrewthomas on 2010-10-04
> **altjx said:**
> Trying to install Java for Ubuntu 10.10 beta 64-bit... Don't bash me, if you know how with 10.4, please help if you can.

.How did you try to install it?  

What commands did you use?

---

### Post by altjx on 2010-10-04
> **andrewthomas said:**
> How did you try to install it?  

What commands did you use?

Used the commands off the java instructions site.

```
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0_02-linux-amd64-rpm.bin
Verify that you have permission to execute the file. Type:
ls -l
 
To start the installation process, type:
./jre-1_5_0_02-linux-amd64-rpm.bin 
```

---

### Post by andrewthomas on 2010-10-04
Get rid of all that and follow this

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU)

---

### Post by gandaran on 2010-10-04
> **altjx said:**
> Used the commands off the java instructions site.

```
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0_02-linux-amd64-rpm.bin
Verify that you have permission to execute the file. Type:
ls -l
 
To start the installation process, type:
./jre-1_5_0_02-linux-amd64-rpm.bin 
```
what! you succeeded in install a rpm package in ubuntu? it's possible but you will have to be a very experienced linux user, so I have doubts you really did install it and even if installed it probably wouldn't work, the correct package for ubuntu would be just the .bin file not the .rpm.bin
any way the best easy way to install java is from the system repositories, I believe the sun-java package has been uploaded to ubuntu 10.10 repositories now, go to software sources and enable the achive.canonical partner repository then update the package list, after enabling and updating the repo you can find the sun-java packages in synaptic or software center. 
or use apt-get to install the java
```
sudo apt-get install sun-java6-plugin
```

---

### Post by oldos2er on 2010-10-04
You want the *.bin file, not *.rpm. Then follow the instructions here: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-)

---

