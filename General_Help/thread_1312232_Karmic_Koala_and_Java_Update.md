---
title: "Karmic Koala and Java Update"
date: 2009-11-03
forum: General Help
---

### Post by jarame on 2009-11-03
So I have Ubuntu Karmic Koala and apparently  Java updated to version "jre1.6.0_16" and I cannot upload pics to Facebook because of it. How do I go about updating Java Script through the command prompt? And how do I get the java plugin for firefox?

Thanks

---

### Post by zvacet on 2009-11-03
Search for java-plugin in synaptic and install it from there.

---

### Post by jarame on 2009-11-03
> **zvacet said:**
> Search for java-plugin in synaptic and install it from there.

Yeah it's installed, thats version 6-15.1, but I need ver. 6-16
Anyways to update that?

---

### Post by jpullen on 2009-11-03
Same problem here.  I upgrade to Karmic from Jaunty on 11/1.  I read elsewhere to do the following...but it doesn't work.

# sudo apt-get purge firefox firefox-3.5
# sudo apt-get install firefox
# sudo /etc/init.d/apparmor restart

I also tried...

# sudo apt-get remove sun-java6-jre sun-java6-plugin
# sudo apt-get install sun-java6-jre sun-java6-plugin

This also doesn't work.

My Java Plugin (from about:plugins) is: 

/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so

---

### Post by jarame on 2009-11-04
> **jpullen said:**
> Same problem here.  I upgrade to Karmic from Jaunty on 11/1.  I read elsewhere to do the following...but it doesn't work.

# sudo apt-get purge firefox firefox-3.5
# sudo apt-get install firefox
# sudo /etc/init.d/apparmor restart

I also tried...

# sudo apt-get remove sun-java6-jre sun-java6-plugin
# sudo apt-get install sun-java6-jre sun-java6-plugin

This also doesn't work.

My Java Plugin (from about:plugins) is: 

/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64/libnpjp2.so

So Is there nothing I can do?

---

### Post by Mighty_Joe on 2009-11-04
I see [someone else]("http://ubuntuforums.org/showthread.php?t=1312928&highlight=facebook") complaining about the same thing.

---

### Post by nacholand on 2009-11-05
Hi there guys!

I found the solution (that some actually posted in these forums)

You need to reinstall it manually downloading the Java 6 SE update 17 from the java.sun site
I just did it and now I got it working just fine

Link with info here:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Hope it helps! (if it didn't already)

---

