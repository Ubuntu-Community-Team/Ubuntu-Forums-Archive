---
title: "Eclipse and superuser (root) privileges"
date: 2012-07-01
forum: General Help
---

### Post by mark909 on 2012-07-01
Hi people.

I am an happy Ubuntu 12.04 user.

I am developing a java program that needs root privileges to access to libpcap functions (via JnetPcap).

I am using eclipse as IDE and I would like to stick with it.

If I run my program from within Eclipse (installed via the Ubuntu Software Center) without root privileges, it does not work. It works if I run Eclipse with root privileges (sudo eclipse, gksu eclipse).

Now I searched for any cons to this approach and it comes out that running application that way may create problems because of the root user taking ownership of configuration files.

Is there anything I can do? For example any actions to take before or after running gksu eclipse to reset ownership?

Searching on the net I've found a workaround ( [http://askubuntu.com/questions/124963/android-not-building-on-eclipse-neither-intellij-on-12-04-lts/125011#125011](http://askubuntu.com/questions/124963/android-not-building-on-eclipse-neither-intellij-on-12-04-lts/125011#125011) ) that works but it's very dirty. Any alternatives?

thanks.

---

