---
title: "Just can't install java..."
date: 2010-09-26
forum: General Help
---

### Post by silentrock on 2010-09-26
Well,ive tried many and many times with many different packages and i always get the same result "Broken packages" , "X package has no installation candidate" or something like that.

Yesterday i wanted to play minecraft,but OH surprise i dont have java web start,or any kind of java installed.

any help to get through this huge problem?

Thanks,silentrock.

---

### Post by 0N3 on 2010-09-26
sudo apt-get install ubuntu-restricted-extras 

should install java support!

---

### Post by hrickh on 2010-09-26
Make sure you have the Canonical Lucid partner repository enabled ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner)

Then click "Reload" to reload all package info, then install sun-java6-jre and sun-java6-plugin.

That should do it.

R.
==

---

### Post by silentrock on 2010-09-26
Nothing,still the same.


Heres the output for sudo apt-get install sun-java6-jre and sun-java6-plugin 
> silentrock@silentrock:~$ sudo apt-get install sun-java6-jre  sun-java6-plugin
[sudo] password for silentrock: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed
E: Broken packages
silentrock@silentrock:~$ 


---

### Post by 0N3 on 2010-09-26
You have tried?

sudo apt-get install ubuntu-restricted-extras

---

### Post by 0N3 on 2010-09-26
Might also be worth a look

[http://gnome-look.org/content/show.php/Ubuntu+Tools?content=125942](http://gnome-look.org/content/show.php/Ubuntu+Tools?content=125942)

---

### Post by silentrock on 2010-09-27
yep tried that,nothing :/

---

### Post by silentrock on 2010-09-27
> **0N3 said:**
> Might also be worth a look

[http://gnome-look.org/content/show.php/Ubuntu+Tools?content=125942](http://gnome-look.org/content/show.php/Ubuntu+Tools?content=125942)

I installed ubuntu Tools and installed java complete support whats next?

---

### Post by philinux on 2010-09-27
> **silentrock said:**
> yep tried that,nothing :/

```
sudo dpkg --configure -a
```

Post back the errors.

---

### Post by FahadMKS on 2010-09-27
Issue following command to find out current jdk version in apt-get
apt-cache search jdk

Install java JDK and JRE with apt-get install

apt-get install sun-java6-jdk sun-java6-jre

Ubuntu will auto download necessary file from web for installation.

[COLOR=green]Do you want to continue [Y/n]? y Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main java-common 0.28ubuntu3 [78.2kB] Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse sun-java6-jre 6-06-0ubuntu1 [6334kB] Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main odbcinst1debian1 2.2.11-16build1 [66.2kB] Get:4 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main unixodbc 2.2.11-16build1 [289kB] Get:5 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse sun-java6-bin 6-06-0ubuntu1 [27.3MB]  Get:6 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/multiverse sun-java6-jdk 6-06-0ubuntu1 [9625kB]  85% [6 sun-java6-jdk 3208002/9625kB 33%]

[/COLOR]After installation done, jdk and jre will install at [B]/usr/lib/jvm/java-6-sun-1.6.0.06
[/B]Ubuntu help to create a java symbolic link and put in /usr/bin for shortcut access
type java -version, DONE !!

Hope this will help you.

If you didn't understand the steps above, you may take a look on the link [http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/](http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/)
everything there is explained in detail.

---

### Post by silentrock on 2010-09-27
Wait,i installed it,i have java now! thanks guys.

I installed [http://gnome-look.org/content/show.p...content=125942](http://gnome-look.org/content/show.p...content=125942) Uubntu Tools and then Java complete support! it worked thanks!

---

