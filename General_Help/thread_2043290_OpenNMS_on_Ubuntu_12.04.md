---
title: "OpenNMS on Ubuntu 12.04"
date: 2012-08-16
forum: General Help
---

### Post by RockinsonM on 2012-08-16
I'm  running a VM with Ubuntu server 12.04 32 bit. I'm just getting into  Ubuntu having very very minor exposure to it in the past. I have been  using the OpenNMS tutorial installation document found at [www.opennms.org/wiki/installation:grin:ebian#Select_Your_Release_and_Distri  bution]("http://www.opennms.org/wiki/installation:Debian#Select_Your_Release_and_Distribution")

While reading through the install document I noticed that during the  install of Java that the package isn't available on the latest  Debian/Ubuntu releases anymore. The alternative is to either use a  private repository or get the binaries and install them manually. 

I opted to get the binary and install it manually.

After installing OpenNMS the tutorial says to configure Java (tell  OpenNMS which Java to use) using the "/usr/share/opennms/bin/runjava"  command. It then gives an example of the full command (sudo  /usr/share/opennms/bin/runjava -S /usr/lib/jvm/java-6-sun/bin/java)  however that is for if you installed the recommended Sun/Oracle JDK. I  believe this means if you used the package install method which I could  not use, although I may be mistaken there. 

Can someone provide me with the proper full command to continue from here? 

For reference, doing an ls of my /usr/lib/jvm directory shows the following child directories:
java-1.6.0-openjdk-i386 (light blue/cyan text)
java-6-openjdk-common (dark blue text)
java-6-openjdk-i386 (dark blue text)
java-7-openjdk-i386 (dark blue text)

Each of those has at least 1 child application file / directory under  it, I believe 3 of them have a bunch, java-7-openjdk-i386 just has one  that says javaws. If you guys would need me to drill down to a lower  level on those to help let me know and I'll list them out.

---

### Post by dino99 on 2012-08-16
sudo update-alternatives --config java

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by RockinsonM on 2012-08-16
Thanks for the response, that got it taken care of. 

Now that it is up and running, the tutorial says to have it scan itself. It provides a relatively lengthy command to do this, which I have had to modify slightly in order to use my specific directory as it didn't match their suggested location, however they use a variable in their command for you to insert your own path. Anyway, the command reads:

perl $OPENNMS_HOME/bin/send-event.pl \ --interface YOUR-OPENNMS-IP \ uei.opennms.org/internal/discovery/newSuspect

I've tried the command several different ways, using -i instead of --interface, trying sudo to start, trying to run the command from different locations (i.e. home directory) with the full path, removing full path, just using perl send-event.pl and running it from the $OPENNMS_HOME directory.

The following is what appears when I attempt to run the command:
*** " --interface" does not appear to be a valid UEI
Usage: /usr/share/opennms/bin/send-event.pl <UEI> [host] [options]
It then lists the options
Example: Force discovery of a node:
send-event.pl \
--interface 172.16.1.1 \
uei.opennms.org/internal/discovery/newSuspect

---

### Post by RockinsonM on 2012-08-20
Bump

---

