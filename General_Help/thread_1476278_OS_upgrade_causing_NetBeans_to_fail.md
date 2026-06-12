---
title: "OS upgrade causing NetBeans to fail"
date: 2010-05-07
forum: General Help
---

### Post by beagler on 2010-05-07
Hey guys. I recently upgraded to 10.04 and now netbeans is not working. It worked fine the first restart after i upgraded so i thought all was good. This morning i ran it and it said something about not being able to load some modules. Since then, i've tried uninstalling it, re-installing it, and numerous restarts, all to no avail. I'm gonna try downloading the package from their website and running it from a separate install and see if that helps, but after that, I'm out of ideas. 

Any advice? 

I plan on doing a full reformat soon enough, but i was really hoping to put it off for 3 weeks or so after school and work eases up. I really don't have the time to do it now... any help will be much appreciated. Thanks.
-andy

P.S. When i run it either from the terminal or by clicking on it, it shows the loading screen, then the loading screen dissapears, then nothing else happens. In the terminal, it waits about ten seconds after the screen dissapears and the program seems to exit, since the terminal begins accepting commands once again.

---

### Post by GregBrannon on 2010-05-07
NetBeans may be having compatibility issues with the OpenJDK packaged by default with Ubuntu 10.04.  You might trying installing the Sun JDK to see if that helps.

---

### Post by beagler on 2010-05-07
Thats a good idea. I'll give it a shot. Thanks a bunch.

---

### Post by dracayr on 2010-05-07
You might already have it (It's installed on my system, for example, and I haven't programmed in java for a long time), only not using it. to enable it, use these commands:```
update-alternatives --config java
update-alternatives --config javac
```

dracayr

---

### Post by beagler on 2010-05-07
Thanks for the help guys. I guess i posted prematurely. After downloading the linux package from their site and running the install wizard everything seems to be working normal, possibly because its pointing to a different place for the jdk now. For some reason sudo apt-get was not fixing it and neither was the the software center gui. Anyways, thanks a bunch for the help.

---

