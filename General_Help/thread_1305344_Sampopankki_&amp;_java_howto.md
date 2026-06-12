---
title: "Sampopankki &amp; java howto"
date: 2009-10-29
forum: General Help
---

### Post by Martiini on 2009-10-29
Sampo pankki java login will work after you:
install sun-java6-bin
install sun-java6-plugin

```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so

```
```
cd /usr/lib/firefox-addons/plugins/
sudo ln -s /etc/alternatives/firefox-3.0-javaplugin.so

```

---

