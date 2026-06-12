---
title: "Could not locate Java Virtual Machine"
date: 2009-10-22
forum: General Help
---

### Post by popik90 on 2009-10-22
Hello everyone,
I've installed JDK and Qt Jambi on my system and i get the following error:
Could not locate java virtual machine.Qt Jambi plugins have been disabled.

I've tried reinstalling both JDK and Qt.

What should i do?

I'm running Ubuntu 9.04.

Thanks

---

### Post by radu.ro on 2009-10-22
What does java -v displays when you run it on the terminal? The JVM(s) should be located in /usr/lib/jvm.

---

### Post by popik90 on 2009-10-22
I tried java -v in the terminal.I got the following message:

Unrecognized option: -v
Could not create the Java virtual machine.

---

### Post by radu.ro on 2009-10-22
My bad... It is java -version. Anyway, the output was sent by the JVM. I have no experience with Qt Jambi, but take a look [here]("http://qt.nokia.com/doc/qtjambi-4.4/html/com/trolltech/qt/qtjambi-installation.html#setting-up-the-environment") for details.

Anyway, your JVM works. I have had some Java programs installed where in the launch script I had to write the path to the java home. Something like JAVA_HOME=/usr/lib/jvm/java-sun-1.6.0...

Best of luck in setting Qt Jambi!

---

### Post by popik90 on 2009-10-22
Thank you for your help:)i'll see what i can do

---

