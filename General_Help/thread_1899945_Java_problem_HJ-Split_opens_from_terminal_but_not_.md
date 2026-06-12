---
title: "Java problem? HJ-Split opens from terminal but not with right-click"
date: 2011-12-24
forum: General Help
---

### Post by bark50 on 2011-12-24
I have this problem with other .jar files (e.g., atunes and jajuk installers) but will use HJ-Split as an example.  I'm running Kubuntu 11.10 64 bit.  If I type in the terminal "java -jar /path/to/hjsplit_g.jar", HJ-Split opens.  If instead I right-click on the hjsplit_g.jar, I have options to open it with OpenJDK Java 7 Runtime or OpenJDK Java 6 Runtime. Choosing either one of those gives me a small, bouncing Java icon that disappears after a few seconds, but the application does not load.  Can someone guide me on getting the application to open with a right-click?  Thanks.

---

### Post by bark50 on 2011-12-24
Solved by following Morbius' advice here:  [http://ubuntuforums.org/showthread.php?t=1894473&highlight=JAVA+CLICK]("http://ubuntuforums.org/showthread.php?t=1894473&highlight=JAVA+CLICK")  However, I ended up with two sets of OpenJDK Java 7 Runtime and OpenJDK Java 6 Runtime in my right-click context menu of which the second set actually works.  If anyone knows how to easily get rid of the first two Java Runtime entries from the context menu, please let me know.  But the original problem is solved, so I'm marking this thread as solved.

---

### Post by bark50 on 2011-12-24
Solved the duplicate entries problem in the context menu by deleting the OpenJDK backup files I had created in /usr/share/applications.

---

