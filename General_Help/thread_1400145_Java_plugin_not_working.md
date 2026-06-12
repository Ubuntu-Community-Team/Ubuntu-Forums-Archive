---
title: "Java plugin not working"
date: 2010-02-06
forum: General Help
---

### Post by The Cog on 2010-02-06
I am having trouble getting the java plugin to work on Ubuntu 9.10 (i386 version, on an Athlon CPU).

I am using the stock Firefox 3.6 as downloaded from mozilla. This is installed in /opt/firefox.

I have installed the java SDK as downloaded from Sun in /opt/jdk1.6.0_18. 

In the past, I have always got the java plugin to work by symlinking from the firefox/plugins directory to the jdk's jre/plugin/i386/ns7/libjavaplugin_oji.so file. However, this doesn't seem to work on this latest Ubuntu/firefox. I don't see the java plugin listed in the **about: plugins** browser page.

I also tried linking the libjavaplugin_oji.so from /usr/lib/mozilla/plugins but this didn't work either.

Does anyone know what might be wrong? Any help would be much appreciated.

---

### Post by ratcheer on 2010-02-06
Yes, you are linking the wrong file. Link to current Java file libnpjp2.so, instead.

Tim

---

### Post by The Cog on 2010-02-06
You Sir, are a gentleman and a scholar. 
That worked a treat - thank you.

---

### Post by ratcheer on 2010-02-06
You are welcome.

Tim

---

