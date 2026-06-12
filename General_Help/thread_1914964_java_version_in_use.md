---
title: "java version in use?"
date: 2012-01-25
forum: General Help
---

### Post by ajgreeny on 2012-01-25
I am wondering why the web site [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp) shows that I am still using **sun java6** when I have removed that and now run **openjdk** version as well as the **icedtea plugin**.

Firefox knows that I have changed, as does the rest of my system after running ```
sudo update-binfmts --package sun-java6 --remove jar /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/jexec
``````
sudo update-alternatives --config java
```shows that there are no alternatives to choose from, but that web site shows the plugin as in my screenshot.

Is this normal or is there some residual config I know nothing about which still believes I have the sun version?

---

### Post by efflandt on 2012-01-25
That is likely perfectly normal, so applications looking to see if you have java can tell that you do (sort of) and what version it acts like.  It still does that in 64-bit 11.10 with openjdk 6.  I think 11.10 also has openjdk 7 optionally available, but the only thing I use java for is minecraft, and openjdk 6 works for that.

Not sure if Lucid has any other openjdk version available.

---

### Post by ajgreeny on 2012-01-25
OK, thanks for that;  I did wonder if it was something similar to that and the webpage believes that only the sun-java6 version exists.

I also have no idea if openjdk-7 is available for Lucid and do not really care that much as the version 6 does all I want.

It is interesting to see how much better openjdk and the icedtea plugin are now than they used to be.  I found it difficult to use my bank website in the past with openjdk, but there seems to be no problem with any that I need to use nowadays.

---

