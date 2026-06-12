---
title: "java installed, firefox can't find plugin?"
date: 2011-03-02
forum: General Help
---

### Post by hyeeeeeeeeelp on 2011-03-02
yesterday i downloaded the java .bin file from the website and made it excutable and ran it in terminal... i got the 'done' message at the end of installation, so i restarted Firefox and verified if i had java. well, i got that message talking about missing plugins... i clicked it and click get missing plugins, It didn't find java on my computer!

---

### Post by gandaran on 2011-03-02
installing that java .bin file is a mistake as you can get sun-java from the ubuntu canonical partner repository which includes a browser plugin, the bin file doesn't have the plugin you will have to make a system link for firefox, look in the sun-java website for instructions for firefox.

---

### Post by turtle153 on 2011-03-02
gandaran is right. Open up the Software Centre and search for java, and you can install the top 3 results (Runtime, Web Start and Icedtea Plug-in).

---

### Post by oldos2er on 2011-03-02
Create a link to the plugin ```
ln -s /opt/jre1.6.0_24/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

Modify the path as needed.

---

