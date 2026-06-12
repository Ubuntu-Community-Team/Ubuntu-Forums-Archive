---
title: "weather and hour in ubuntu 11.4"
date: 2011-06-02
forum: General Help
---

### Post by magodiafano on 2011-06-02
Hello I have two problems:
the first is about the weather: how could I add the weather in the panel like in ubuntu 10? (I am using the classical visualization)
the first problem regards the clock... it works but not completely: ie now are14:19 but it shows 14:1 and only an half of 9! i tried moving it but it does not work

---

### Post by johngreth on 2011-06-02
Can you right click and add to panel?
Can you move the clock at all?
Do you have any unusual things like an additional panel or anything on a panel where it normally wouldn't be?

---

### Post by magodiafano on 2011-06-02
> **johngreth said:**
> Can you right click and add to panel?
Can you move the clock at all?
Do you have any unusual things like an additional panel or anything on a panel where it normally wouldn't be?

nope, I have just installed ubuntu 11.4!
The problem  is this:

[IMG]http://img810.imageshack.us/img810/5690/screenshotepu.png[/IMG]

I tried to move the panel but I cant solve the problem!!

And what about the weather?

---

### Post by Frogs Hair on 2011-06-02
```
sudo apt-get install indicator-weather
``` You can also install the application at the link. I have tried both and prefer the PPA . Either one should appear after restart. If you choose the PPA set it to auto start in preferences .[http://www.makeuseof.com/tag/readd-weather-ubuntu-1104s-panel-linux/](http://www.makeuseof.com/tag/readd-weather-ubuntu-1104s-panel-linux/)

---

### Post by johngreth on 2011-06-02
You could try adding individual applets to the top panel and getting rid of the single applet with everything on it. Just right click the clock and click remove from panel, then right click where it was and select "add to panel". "Indicator Applet Complete" is what was there, but you could experiment with the other indicator applets to see if any of them work. The weather report applet should also be in that list.

---

### Post by Maheriano on 2011-06-02
Change the default font size.

---

