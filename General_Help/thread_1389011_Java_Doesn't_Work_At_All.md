---
title: "Java Doesn't Work At All"
date: 2010-01-23
forum: General Help
---

### Post by s3MA00RRNY on 2010-01-23
I've tried installing/removing/purging through apt and Firefox still complains about missing plugins. Also tried IcedTea and that didn't work either. What else should I try?

---

### Post by d3v1150m471c on 2010-01-23
the new adobe java is pure crap. use the version that came out before it. this isn't just a linux issue; it's multiplatform.

---

### Post by rogue_0111 on 2010-01-23
using GNOME

[IMG]http://www.ubuntu.com/include/ubuntu2.png[/IMG]

On your taskbar Click "system", "Administration", the "Synaptic Package Manager".

Type password.

When Synaptic launches, I believe it's "sun-java6-jre"

---

### Post by s3MA00RRNY on 2010-01-30
I tried this already. Look at the OP. Adobe Java??? SUN does Java, not Adobe. If you were talking about Flash being crap, then yeah, it always has, always will be. Unfortunately, we have to put up with it.

---

### Post by wojox on 2010-01-30
Did you install the java 6 plugin:

```
sudo apt-get install sun-java6-plugin
```

---

### Post by s3MA00RRNY on 2010-02-04
Yes, I did. I also have NoScript installed, but I have unblocked the sites I want to view.

---

### Post by Admiral_Payne on 2010-02-04
Perhaps your NoScript is still blocking the java applets, if they are loaded from a different source than the website you've unblocked?

Check the source of those pages to see what the location of those applets is, and try to add an exception rule for those.

Did you try another browser? Or with NoScript disabled?

---

### Post by s3MA00RRNY on 2010-02-19
Update: I recently ran a standalone Java application, so Java does work. The plugin still does not, though.

---

### Post by scouser73 on 2010-02-19
To install the latest version of Sun Java I would recommend you use this method as the Ubuntu repositories won't be updating Sun Java anymore (from what I know): [[COLOR="Red"]**Install latest version of Sun Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10")

---

### Post by ford074 on 2010-02-19
Thanks! This worked great!!!

---

### Post by chill32 on 2010-02-19
if your using Mozilla it should automaticly find the missing plug-in

---

### Post by s3MA00RRNY on 2010-02-24
I tried the manual setup mentioned and it did not work. I will have to try it again because I may have done something wrong.

---

