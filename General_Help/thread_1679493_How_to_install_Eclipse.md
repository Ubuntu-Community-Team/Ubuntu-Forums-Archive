---
title: "How to install Eclipse"
date: 2011-02-01
forum: General Help
---

### Post by SivaCoHan on 2011-02-01
Hey,friends . I come from China .
I find it's great using Ubuntu.
It is my first time posting Thread here.

I want to learn J2EE.
I used to use MyEclipse 6.5 when I use windows xp.

now I have problems, in install Eclipse

1. I want to use Sun jdk and jre , I tried many times to uninstall OpenJDK but failed.could help me?
2. Tomcat . I use sudo apt-get install tomcat6 .but Eclipse doesn't get the server name .
3. In MyEclipse , I can make a "web project" when i want to use J2ee . what should I start ,when I use Eclipse?

Thanks

---

### Post by veggen on 2011-02-01
1. Sun Java is in the partner repo, but if you want the latest version do this:
```

sudo add-apt-repository ppa:sun-java-community-team/sun-java6

sudo apt-get update

sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk
```
after that read [Ubuntu guide on Java](https://help.ubuntu.com/community/Java), specifically the "Choosing the default Java to use" part. In short, you run ```
sudo update-java-alternatives -s java-6-sun
```.
You can easily remove OpenJDK from App Center or Synaptic.

2. I don't understand this part? Did you install Tomcat successfully or not?

3. Get Eclipse for Java EE, it's a regular version with Java EE related plugins already integrated: [32bit](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/helios/SR1/eclipse-jee-helios-SR1-linux-gtk.tar.gz), [64bit](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/helios/SR1/eclipse-jee-helios-SR1-linux-gtk-x86_64.tar.gz).

---

### Post by SivaCoHan on 2011-02-01
1.About JDK
lee@lee-laptop:~$ sudo update-alternatives --config java
&#26377; 3 &#20010;&#36873;&#39033;&#21487;&#29992;&#20110;&#26367;&#25442;&#39033; java (&#25552;&#20379; /usr/bin/java)&#12290;

  &#36873;&#25321;       &#36335;&#24452;                                    &#20248;&#20808;&#32423;  &#29366;&#24577;
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      &#33258;&#21160;&#27169;&#24335;
  1            /home/lee/jdk1.6.0_23/bin/java             300       &#25163;&#21160;&#27169;&#24335;
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      &#25163;&#21160;&#27169;&#24335;
* 3            /usr/lib/jvm/java-6-sun/jre/bin/java       63        &#25163;&#21160;&#27169;&#24335;
I don't know how to translate that into English. &#33258;&#21160;means auto . I don't know what the number means;


2. In 10.04 Ubuntu china (the chinese forums) says the tomcat6 was divde into 2 parts so , Eclipse doesn't accept this server.

3. Yeah, I got the right version . Java EE helios . but i didn't find the buttom or something about shutdown or restart Tomcat server.

---

### Post by SivaCoHan on 2011-02-01
Do you know where I can find a Guide about how to Install Eclipse & JDK(Sun) & Tomcat6
the books in China teaching Java all based on Windows .

---

