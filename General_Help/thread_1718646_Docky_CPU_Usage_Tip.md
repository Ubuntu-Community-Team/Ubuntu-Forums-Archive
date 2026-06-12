---
title: "Docky CPU Usage Tip"
date: 2011-03-31
forum: General Help
---

### Post by dwitkin on 2011-03-31
I wanted to share a solution I found to address a condition in Docky that generated consistent CPU usage even when the application should have been doing nothing.

Several weeks after installing and running Docky successfully in Ubuntu 10.10, I started noticing the Docky service consistently used 6 - 8 percent of my CPU even when the mouse was not above Docky and in my view the app should have been using 0% of CPU. Worse, when I looked at total CPU usage since boot, Docky was #1 on the list, using more CPU cycles than any other application.

After some trial and error, I discovered **the issue was the Docky weather widget**. Apparently, when the weather widget is not configured with a valid weather station, Docky goes into some type of loop doing something it shouldn't and is eating up CPU time. I assigned a valid weather station using the widget configuration screen and my "at rest" Docky CPU usage dropped to 0%.

---

