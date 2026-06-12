---
title: "Can't find Java"
date: 2006-06-08
forum: General Help
---

### Post by forrestcupp on 2006-06-08
I recently did a clean install of Dapper release.  I have enabled my universe and multiverse repos, and I cannot find sun-java to install it.  Can anyone tell me why it's not in my list?  Doing a search for java in syaptic doesn't bring it up.  I can't even find the Blackdown j2rel package.

---

### Post by taurus on 2006-06-08
Use Automatix to install java and anything else (codecs, plugins, multimedia, etc.) on your Dapper then.  ;)

---

### Post by asimon on 2006-06-08
```
# apt-cache search sun-java
sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin - The Java(TM) Plug-in, Java SE 5.0
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files

```
It's there, double-check that you have the multiverse repository activated.

---

### Post by nix4me on 2006-06-08
Yes, its there.

nix4me

---

### Post by forrestcupp on 2006-06-09
Thanks guys.  I don't know what happened, but when I just checked again, it was there.

---

