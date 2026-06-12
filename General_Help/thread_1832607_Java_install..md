---
title: "Java install."
date: 2011-08-25
forum: General Help
---

### Post by kensclark15 on 2011-08-25
I tried uninstalling OpenJDK but I can't find out how. I then tried to install Java from Sun. I got the .bin file and put it in my home directory and typed    sh (then the file name) and it extracted everything and it looked like it installed. But now I can't run anything with it. Can you tell me how to uninstall OpenJDK then install Sun's Java? Thanks, I run Ubuntu 11.04 64-bit.

---

### Post by Miljet on 2011-08-25
You can do everything you want from Synaptic package manager. Search for java, then remove icedtea6.plugin. On the top toolbar, go to Settings -> Repositories, click on Other Software tab and enable the partner repository.
Close that window and click on Reload. Then search for sun-java6. You want to install sun-java6-jre, sun-java6-plugin, and sun-java6-fonts.

---

