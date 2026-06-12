---
title: "How do I get Java working in Opera?"
date: 2011-11-16
forum: General Help
---

### Post by bastones on 2011-11-16
I have the IcedTea plugin for Java which from searching around only works in Firefox. I have tried installing other Java plugins and manually downloading and installing Java from the Java website with no luck. How can I get Java working in Opera?

Thanks.

---

### Post by Frogs Hair on 2011-11-16
The only suggestion I found . is open quick preferences and make sure that plug-ins are enabled .
[http://mindprod.com/jgloss/opera.html#JAVA](http://mindprod.com/jgloss/opera.html#JAVA)

---

### Post by gradinaruvasile on 2011-11-16
It works with Opera for me.

---

### Post by Gremlinzzz on 2011-11-16
Iced Tea plugin for Java doesnt work for all sites.
use    
sudo apt-get install sun-java6-jre sun-java6-plugin
you would have to remove icetea plugin cause they bump heads:popcorn:

---

### Post by bastones on 2011-11-16
> **Gremlinzzz said:**
> Iced Tea plugin for Java doesnt work for all sites.
use    
sudo apt-get install sun-java6-jre sun-java6-plugin
you would have to remove icetea plugin cause they bump heads:popcorn:

Cheers. Just as confirmation for others, I first needed to install a repository that had these packages:

```
sudo add-apt-repository ppa:ferramroberto/java
```

You can remove package sources via:

```
sudo gedit  /etc/apt/sources.list
```

And if it isn't listed there it should be in:

```
sudo gedit  /etc/apt/sources.list.d
```

Reference:

[http://www.upubuntu.com/2011/06/how-to-install-sun-java-6-jrejdk-on.html](http://www.upubuntu.com/2011/06/how-to-install-sun-java-6-jrejdk-on.html)

[http://ubuntuguide.net/install-sun-java-6-jrejdk-from-ppa-in-ubuntu-11-04](http://ubuntuguide.net/install-sun-java-6-jrejdk-from-ppa-in-ubuntu-11-04)

---

