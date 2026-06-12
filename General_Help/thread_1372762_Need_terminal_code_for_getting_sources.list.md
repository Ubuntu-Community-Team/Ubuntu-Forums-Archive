---
title: "Need terminal code for getting sources.list"
date: 2010-01-04
forum: General Help
---

### Post by DougieFresh4U on 2010-01-04
Have not used Xubuntu for a couple of years.
Using an older machine I have finally been able to get something installed on it, Xubuntu Hardy. I would like to try to upgrade to Intrepid using the terminal. I **DO NOT** want to use** update manager**.
Would some one please provide me with the code to access the sources list. I knew what it was a couple of years ago but have since forgotten. 
Thanks

---

### Post by MelDJ on 2010-01-04
this? sudo gedit /etc/apt/sources.list
[]("http://www.google.com.my/url?q=http://ubuntuforums.org/archive/index.php/t-207231.html&ei=4LJCS-iBEoqOkQWuyLGdDQ&sa=X&oi=forum_cluster&resnum=1&ct=result&cd=1&ved=0CAkQrAIoADAA&usg=AFQjCNHaNHmuaGG-_vVeKoPx3T7E2vnrfw")

---

### Post by mechro on 2010-01-04
To edit the sources list...

**gksudo gedit /etc/apt/sources.list**

---

### Post by DougieFresh4U on 2010-01-04
I am using **Xbuntu**, I thought the commands were different than Ubuntu. I thought the words 'mousepad' or some thing were in the command I am seeking.
Thanks for the replies :)

---

### Post by mechro on 2010-01-04
If you've got the mousepad editor in Xubuntu then replace gedit with mousepad...

**gksudo mousepad /etc/apt/sources.list**

---

### Post by DougieFresh4U on 2010-01-04
> **mechro said:**
> If you've got the mousepad editor in Xubuntu then replace gedit with mousepad...

**gksudo mousepad /etc/apt/sources.list**

Thank you!!!:)

---

