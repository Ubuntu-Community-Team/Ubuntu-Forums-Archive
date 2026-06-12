---
title: "java and flash don't work"
date: 2009-11-03
forum: General Help
---

### Post by ravynchylde1960 on 2009-11-03
I'm running 9.10 64-bit with Firefox 3.5.4. About:plugins says Flash is there but when I go to a flash site like YouTube, the site loads but nothing happens.

About:plugins also says the java plugin's not there.

This is driving me crazy.

I have tried uninstalling all java from my machine, including plugins and reinstalling.
Didn't work. I have tried the sun-java plugin, the icedtea plugin, the javaplugin from the Sun site itself... didn't work.

When I tried update-alternatives --config java, I got:

root@leslie-desktop:/usr/lib/xulrunner-addons/plugins# update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                            Priority   Status
------------------------------------------------------------
  0            /usr/bin/gij-4.4                 1044      auto mode
* 1            /opt/java/jre1.6.0_16/bin/java   1         manual mode
  2            /usr/bin/gij-4.4                 1044      manual mode

Which is the java I downloaded and installed from the Sun site. I'm guessing that a symlink is wrong or missing?

---

