---
title: "Need help installing Java Plug v6 upd18"
date: 2010-03-12
forum: General Help
---

### Post by dwcbrq on 2010-03-12
Hello,

I need help on installing Java Plug-in, version 6, upd 18 so I may play games on pogo.com.

Can I make this happen with a simple apt-get?  I don't want to sym link all over the place.  That is insane.

Thanks.

EDIT:  Here is my output when I run apt-get, giving it what I was told to give it...

d@d-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

---

### Post by Uncle Spellbinder on 2010-03-12
This worked perfectly for me on Karmic and Lucid. Installed the latest Java 6 update 18 -

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-) 32 Bit

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-) 64 Bit

---

