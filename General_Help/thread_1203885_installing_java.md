---
title: "installing java"
date: 2009-07-03
forum: General Help
---

### Post by asliyanage on 2009-07-03
i need to install java to my new ubuntu 9.0.can anyone tell me the way how to install jdk to linux?it is helpful if u tell the steps also?because i am new to linux?thanks

---

### Post by credobyte on 2009-07-03
Open Terminal and paste in this command :
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
```

---

### Post by asliyanage on 2009-07-03
can u tell me is it possible to chang the path of installing jdk in our ubuntu OS.i mean we can install java in windows as our wish ?.is it possible in ubuntu?if yes tell me how to install java to folder that is make by me?any way normall where should the installing software lying?i mean in windows it is in C\programming files

---

### Post by Bradj47 on 2009-07-04
I don't know if it's possible to change the install location from a command like that or even a .deb file. I do know that theres a different location depending on the application. You can find out where any application is installed by typing: ```
which <app>
``` in a terminal. I.E.:
```
brad@rockstar:~$ which java
/usr/bin/java

```

I think you can choose where the application goes if you compile from source but I'm not sure Sun made Java open source.

---

