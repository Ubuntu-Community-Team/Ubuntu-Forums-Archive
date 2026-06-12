---
title: "Java not working in Lucid"
date: 2010-08-30
forum: General Help
---

### Post by januutreurle on 2010-08-30
I could not get JAVA working in Lucid. Installed **OpenJDK Java 6 Runtime** and **OpenJDK Java 6 Webstart** from Ubuntu Software Center but no Java showed up in Firefox's about:plugins.

After searching for hours in numerous forums (mostly dealing with sun-java) I got the idea that the web-browser plugin could be missing. And so I found the following solution:

Install **icedtea6-plugin** With Synaptic Package Manager (or **Icedtea java plugin** from Ubuntu Software Center).

Now JAVA is running smoothly.

Thought it is a good idea to share my findings with the community.

---

### Post by wojox on 2010-08-30
Thanks. Instead of wasting precious hours try the Search in the top right corner. [Java Lucid]("http://ubuntuforums.org/search.php?searchid=75607477")

---

### Post by januutreurle on 2010-08-30
> **wojox said:**
> Thanks. Instead of wasting precious hours try the Search in the top right corner. [Java Lucid]("http://ubuntuforums.org/search.php?searchid=75607477")

You are right. Unfortunately I searched for **Java Firefox** and missed somehow the Icedtea :(. Writing this .. Is there a way to add more labels (f.e. Firefox) to this thread?

---

