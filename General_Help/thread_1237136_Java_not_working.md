---
title: "Java not working"
date: 2009-08-11
forum: General Help
---

### Post by deadlydes on 2009-08-11
I have just done a clean install of Jaunty on my system but now i cant get Java in Firefox to work.

I have been following this page which has been linked to many times [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

Basically its
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

then i can see it appears to be installed
java -version gives

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08 )
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

But when i go to a webpage requiring Java it doesnt work.

Any help appreciated

---

### Post by mthalis on 2009-08-11
Are you enable Java in you're browser? firefox preference -> content -> enable Java

---

### Post by deadlydes on 2009-08-11
> **mthalis said:**
> Are you enable Java in you're browser? firefox preference -> content -> enable Java

yeah thats been done.

---

### Post by mthalis on 2009-08-11
Try this command 
> sudo update-java-alternatives -s java-6-sun

---

### Post by AoA Linux on 2009-08-11
When I had this problem, I went into the add/remove package manager, and typed in "java".  Make sure all of the java options are installed, including the 6.0 java plugin.  Make sure you have all available applications selected at the top of the package manager and not just canonical supported ones.

---

### Post by deadlydes on 2009-08-12
> **mthalis said:**
> Try this command

That seemed to have worked to a certain extent.
now if i goto a java test page it works and i have version 6 update 14 

But a site i really want to get to work is [http://www.accuradio.com/](http://www.accuradio.com/)
when clicking on any of the radio stations a window pops  up but no music plays and at the bottom of the window there is a message 'javascriptvoid (0);'

any ideas on that?
Thanks

---

