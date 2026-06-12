---
title: "Not able to complete JRE installation"
date: 2011-07-16
forum: General Help
---

### Post by inmank on 2011-07-16
I tried to install jre using the following command


sudo apt-get install sun-java6-jre

the download is sucessful, after that i got the "package configration" screen contans details and Ok at last. I am not able to close the screen and continue the installation.

If I tried to close the screen, it shows the process is still running.

Attached the screen shot for more details,

kindly help

---

### Post by gandaran on 2011-07-16
press the tab key to highlight the 'OK' then enter to accept the licence.

---

### Post by karthick87 on 2011-07-16
To install Java in Ubuntu 10.10, follow these steps:

1. Press ALT + F2 and enter this:

```
gksu /usr/bin/software-properties-gtk
```


2. Then go to the "Other Software" tab and the first repository on the list should be "http://archive.canonical.com/ubuntu maverick partner" - enable this repository (both lines). Then click "Close" and when prompted, click "Reload".

3. Then simply search for "sun java" in Ubuntu Software Center and install JRE and the Java plugin, or install it from a terminal using the following command:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by inmank on 2011-07-16
Thanks, working fine

---

### Post by karthick87 on 2011-07-16
Please mark this thread as solved..

---

