---
title: "JGrasp How do I get the applet button to show up?"
date: 2012-01-19
forum: General Help
---

### Post by Detonator on 2012-01-19
How do I get the apple icon and the half-apple/ladybug icon on my tool  bar. I installed the most recent version of JDK, which is "Java SE JDK  7u2". I put everything in the same folder where I installed jGrasp. What  do I need to do now to get the 2 icons to show up, because I want to  use applets. Tell me in details please.

---

### Post by lbarowski on 2012-01-19
In recent versions of jGRASP, the "Run" and "Debug" buttons will determine if your file is an applet, application, or both, or if you are using a project and have not designated a main file, it will find any files in your project with application entry methods or that are applets. If it finds multiple ways to run, it will give you a choice. So just use the regular run and debug toolbar items. Note that the tool hints for those buttons also indicate that they will run an application or applet.

If your class does not inherit directly from Applet or JApplet, it will not be flagged as an applet and you'll have to use the menu item "Run" / "Run as Applet" to run it.

---

