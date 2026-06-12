---
title: "More memory to java"
date: 2012-04-16
forum: General Help
---

### Post by canhoto on 2012-04-16
Hi.

How can I allocate more memory to a online java applet like this one: [http://www.osm-3d.org/map.htm](http://www.osm-3d.org/map.htm) ?

Is there a way to allocate mor memory to all the java apps and applets at once?

Thanks

---

### Post by lykeion on 2012-04-18
Are you running OpenJDK Java or Oracle Java?

If Oracle, you can run the Java ControlPanel (located in the /jre/bin folder of where you installed Java). In the Java tab click button Settings... then double-click in the Java Runtime Parameters field to set a memory parameter, example:
```
-Xms128m -Xmx256m
```
The -Xms128m specifies the starting size of the Java heap (128 MB) and -Xmx256m specifies the maximum size.

Not sure about OpenJDK, perhaps someone else knows?


P.S OSM 3D map was pretty cool

---

