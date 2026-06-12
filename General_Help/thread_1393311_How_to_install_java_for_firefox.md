---
title: "How to install java for firefox?"
date: 2010-01-29
forum: General Help
---

### Post by dogdo on 2010-01-29
Hi 

Is this the real java website [http://java.com/en/download/linux_manual.jsp?host=java.com&locale=en-US](http://java.com/en/download/linux_manual.jsp?host=java.com&locale=en-US) or is it malware?

---

### Post by gradinaruvasile on 2010-01-29
And why should it be malware?

The firefox plugin is installed by installing the sun-java6-plugin package.

But for Firefox 3.6/Chromium the java plugin enabling needs a link to be created:

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugin/

in a terminal (if you are using the standard i386 version).

---

