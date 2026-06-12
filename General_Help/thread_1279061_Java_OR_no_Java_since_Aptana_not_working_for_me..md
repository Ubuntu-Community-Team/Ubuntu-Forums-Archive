---
title: "Java OR no Java since Aptana not working for me."
date: 2009-09-30
forum: General Help
---

### Post by rahul23 on 2009-09-30
Hellow guyz.
  I just installed ubuntu remix on my laptop (by dumping xp) and  was trying to install Aptana IDE but it says JRE runtime not found but since Open Office also requires JRE and its working fine , then what part of story i am missing here ??

Thanks In Advance.

---

### Post by anagor on 2009-09-30
Openoffice can live with pretty much any jre there is, while aptana recommends the sun's jre.

You can try installing openjdk-6-jre, maybe it will be sufficient, or instead of the standalone version of aptana you can try installing the eclipse plugin version, which of course requires you to install eclipse first, but eclipse is in the repositories already, so there should be no problem installing it, and it will pull all the needed dependencies with it.

hope this helps.
on a side note: why aptana?

---

### Post by credobyte on 2009-09-30
Java isn't installed by default.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by rahul23 on 2009-10-09
> **anagor said:**
> Openoffice can live with pretty much any jre there is, while aptana recommends the sun's jre.

You can try installing openjdk-6-jre, maybe it will be sufficient, or instead of the standalone version of aptana you can try installing the eclipse plugin version, which of course requires you to install eclipse first, but eclipse is in the repositories already, so there should be no problem installing it, and it will pull all the needed dependencies with it.

hope this helps.
on a side note: why aptana?
Your Idea is excellent, on the note side I think new Aptana 1.5 is an great IDE , maybe 
you had a bad experience with the old version so I suggest you to give it a try.

> **credobyte said:**
> Java isn't installed by default.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
this worked , actually the blue screen which shows up was the problem since i was unaware TAB button on keyboard can be so usefull.

---

