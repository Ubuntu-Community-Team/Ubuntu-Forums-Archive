---
title: "How can I start a .jar file by double-clicking it? Ubuntu 12.04 LTS"
date: 2012-04-29
forum: General Help
---

### Post by XHotSniperX on 2012-04-29
Hello

I installed Ubuntu 12.04 LTS and I really like it. A lot has changed since Ubuntu 8.

Everything works fine until now except launching .jar files. I want to launch .jar files by double-clicking it. Like on Windows.

I have installed Java 7 Update 4 thanks to this [guide]("http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/"). 

That worked fine and typing "java -version" in terminal gives me the right answer. Eclipse works fine and also Firefox Web Java Applets.

But when I right-click a .jar file and choose Properties-->Open With there is no option to start it with Java. When I install OpenJDK I can choose OpenJDK...

But I don't want to have two different Java versions installed. I want that one from Oracle's website.

So how can I add Oracle Java to the Applications list?

Thanks
__

---

### Post by XHotSniperX on 2012-04-29
push

---

### Post by vishnumrao on 2012-05-01
1. Open Firefox
2. Go to this page: [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
3. Click on verify java
4. Firefox will say you don't have java and prompt you to install icedtea7 java plugin.
5. Install

Or open software center and install the "IcedTea Java Web Start"

Then you will have java installed. Then go open your .jar

---

### Post by oboedad55 on 2012-05-01
> **XHotSniperX said:**
> Hello

I installed Ubuntu 12.04 LTS and I really like it. A lot has changed since Ubuntu 8.

Everything works fine until now except launching .jar files. I want to launch .jar files by double-clicking it. Like on Windows.

I have installed Java 7 Update 4 thanks to this [guide]("http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/"). 

That worked fine and typing "java -version" in terminal gives me the right answer. Eclipse works fine and also Firefox Web Java Applets.

But when I right-click a .jar file and choose Properties-->Open With there is no option to start it with Java. When I install OpenJDK I can choose OpenJDK...

But I don't want to have two different Java versions installed. I want that one from Oracle's website.

So how can I add Oracle Java to the Applications list?

Thanks
__

Did you follow all the directions and make sure to "update -alternatives"?
Have a look here: [http://ubuntuguide.net/install-oracle-javajdk-7-in-ubuntu-12-04-precise-11-10-oneiric](http://ubuntuguide.net/install-oracle-javajdk-7-in-ubuntu-12-04-precise-11-10-oneiric)

---

