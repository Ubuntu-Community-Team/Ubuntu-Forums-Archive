---
title: "Malicious Code? Probably not.."
date: 2010-11-26
forum: General Help
---

### Post by UOutCailin on 2010-11-26
I'm pretty new to Ubuntu, so I just wanted to verify this line of code, which is supposed to grab Sun Java and install it on my machine.

 ```
cd /opt/java/64 sudo ./jre-6u22-linux-x64.bin
 sudo update-alternatives --install "/usr/bin/java" "java" "opt/java/64/jre1.6.0_22/bin/j*ava" 1
 sudo&#65279; update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_22/bin/*java" 1
 sudo update-alternatives --set java /opt/java/64/jre1.6.0_22/bin/j*ava
 mkdir ~/.mozilla/plugins
 sudo apt-get remove icedtea6-plugin
 rm ~/.mozilla/plugins/libnpjp2.so
 ln -s /opt/java/64/jre1.6.0_22/lib/a*md64/libnpjp2.so ~/.mozilla/plugins/

```After reading through that sticky about evil commands and whatnot, I decided to ask even though i don't see anything wrong with it..

Can someone please verify this for me?

---

### Post by eric3_14159 on 2010-12-24
Assuming you trust your jre-6u22-linux-x64.bin file (if you're paranoid then I suggest checksumming it), it should be safe.

---

### Post by mastablasta on 2010-12-24
this is installing original Sun Microsystems Java and removing IcedTea (opensource Java).

---

