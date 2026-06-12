---
title: "openJDK ggrrrrrr"
date: 2010-01-12
forum: General Help
---

### Post by whitetimer on 2010-01-12
Hi All

I have just clean installed karmic and have installed jdk-6-update-17 and set all the environmental variables and checked with java -version ... It was perfect.

Now i have installed eclipse and its placed openJDK as the java -version ... ggrrrr

How do i change this back to my original settings ?

Many thanks :D

---

### Post by jamesbannon on 2010-01-12
> **whitetimer said:**
> Hi All

I have just clean installed karmic and have installed jdk-6-update-17 and set all the environmental variables and checked with java -version ... It was perfect.

Now i have installed eclipse and its placed openJDK as the java -version ... ggrrrr

How do i change this back to my original settings ?

Many thanks :D

Have a look at ```
man 8 update-alternatives
```. The --config option looks like the one you want, since that allows you to change link settings interactively. (It's a long time since I've used that command. Last time I saw it when was I was using Fedora 10. I just noticed that Ubuntu uses it).

---

