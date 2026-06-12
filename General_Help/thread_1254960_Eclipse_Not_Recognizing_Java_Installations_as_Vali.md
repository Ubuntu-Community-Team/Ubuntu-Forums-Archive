---
title: "Eclipse Not Recognizing Java Installations as Valid JREs"
date: 2009-08-31
forum: General Help
---

### Post by tim22b on 2009-08-31
I installed Eclipse 3.5 according to a webpage out there (I already closed it), but it appears to work.  It's installed to /opt/eclipse3.5/. I have the sun-java5 and sun-java6 packages installed, and before that had the sun jdk 1.6 update 16 installed via the bin from sun's website.  After messing around with various files, making sure JAVA_HOME was getting set, and going through the update-alternatives --config java, and update-java-alternatives, Eclipse appears to start with no problem.  I had to set the JAVA_HOME variable in ~/eclipse/eclipserc to get it to recognize a jdk to start when I had the jdk installed from the bin file, but it did start.  I have a problem now where it's attempting to run code on the gcj jre1.5.

This wouldn't be as big of a problem except that when I call the showOptionDialog method (creates a simple dialog box), it looks wierd and refuses to close on its own.  When I look at the "Installed JREs" under preferences, it only lists the gcj1.5 jre.  I click Search (Add also produces the same outcome), and point it to the base directories for sun-java6 and sun-java5, and the .../jre/ directories, and it says no JREs found.  If I attempt to run the application via java from the command line, it looks and works normally.

Does anyone know if I'm not setting something correctly with the java installs or if it's an eclipse problem or anything?

Thanks!

---

