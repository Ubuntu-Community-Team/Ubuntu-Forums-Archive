---
title: "Java Runtime Enviroment"
date: 2011-06-13
forum: General Help
---

### Post by Barajqial on 2011-06-13
Hey guys I searched to forums a bit but haven't really found anything that helps in my case. 
 Here is what's going on I have a supermicro mobo that has the ability to run a console redirect through a web interface.  The problem is that this requires java to use, and I cannot get firefox to recognize that I have a java runtime environment installed.  I have downloaded java from here

[ http://java.com/en/download/linux_manual.jsp?locale=en ]("http://java.com/en/download/linux_manual.jsp?locale=en")

 I extract the bin no problem to the /usr/java directory making sure it is executable and all that good stuff no issues.  Then nothing happens supposedly I am to get a prompt with the license agreement and what not, but nothing. 

 So thinking that since it did actually make the directory anyway I just went ahead and made the symbolic link from the java dir that was made to the appropriate firefox plugin locale using

```
sudo ln -s /usr/java/jre1.6.0_26/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

nada no java no nothing every time i try and verify the install it just hangs.
Im running 11.04 fully updated with firefox 4.0.1.
 Anyone have any ideas?

-bar

---

### Post by gandaran on 2011-06-13
why not just install java from package manager instead downloading from java website, there are two javas in the software center, sun-java and openjdk java, both have a plugin for firefox, icedtea plugin for openjdk and sun-java-plugin

---

### Post by sammiev on 2011-06-13
I like installing [Sun Java]("http://sites.google.com/site/easylinuxtipsproject/java") using this method and when last checked I was 2 versions up from the package manager. GL :)

---

### Post by Barajqial on 2011-06-13
Okay Dokay what ended up working for me was it turns out a utility that was provided by Sunmicrosystems called IPMI View it came bundled with Java iKVM viewer and after a little set-up it now works flawlessly. :D

---

