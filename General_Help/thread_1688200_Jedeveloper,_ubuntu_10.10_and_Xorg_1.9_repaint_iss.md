---
title: "Jedeveloper, ubuntu 10.10 and Xorg 1.9 repaint issue"
date: 2011-02-15
forum: General Help
---

### Post by Ddnh on 2011-02-15
Hi,

 I just upgraded one machine Dell Optiplex 755 to Ubuntu Maverick 10.10  with Java 1.6.0.23 and Oracle JDeveloper 11g 11.1.1.3.0. Since then, my  Jdev is not working properly from a graphic point of view. When you  start it , it doesn't show all the icons in the console. You have to  pass the mouse over them to be shown, and as soon as you  minimize/maximize the window, those are hidden again. It's like Java or  Jdev are not sending the correct commands to repaint the screen or the X server is not understanding them correctly.

I don't have any similar graphic issue with any other application like  openOffice or Oracle SQL datamodeler. But I do have the same issue with  the Oracle SQL developer application, the icons are not shown unless you  pass the mouse over them and they disappear if you minimize/maximize  the window. Jdev and SQL Developer have a similar interface.

 The drivers of the graphic card, ATI Radeon HD 2400 XT, are up to date  and I already tried with different tweakings in the graphical  properties. The Xorg server is 1.9.0

Does any of you have any suggestion/solution?

This didn't happen with an Ubuntu 9.10 and old versions of java and Jdev installed in the same machine.


 Greetings and thank you.

---

### Post by Ddnh on 2011-02-15
Does someone has any idea?

---

### Post by vhogemann on 2011-12-05
Hi there,

I have the exactly same issues as you. I've tried changing the JVM to IcedTea, JRockit and Sun... but nothing seems to work.

I'll keep trying and post here any solution that comes by.

---

