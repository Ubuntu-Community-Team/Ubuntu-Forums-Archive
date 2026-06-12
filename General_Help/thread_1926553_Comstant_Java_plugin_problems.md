---
title: "Comstant Java plugin problems"
date: 2012-02-16
forum: General Help
---

### Post by IronArjen on 2012-02-16
Once in a while the Java plugin, or the complete Java, I don{t know stops working. Websites simply put like 

Java seems to be disabled or not installed in your browser 

This has something to do with upgrades but I cannot find how to fix it. I have 20 machines running in my student lab and cannot find the difference in all the different setups. Any idea?

---

### Post by QIII on 2012-02-16
Did you install Sun Java or OpenJDK from the repos?

If you are using the OpenJDK plugin called IcedTea, then there are going to be websites that won't work with it.  They expect Sun Java.

Could you run

```
java -version
```

in the terminal and post the results?

---

### Post by IronArjen on 2012-02-16
Should be Sun

java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Client VM (build 20.1-b02, mixed mode, sharing)

---

### Post by Gremlinzzz on 2012-02-16
the plugin of sun Java?
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

just copy and paste
its updated to 1.6.0_30

---

### Post by QIII on 2012-02-16
First, let's see if we can resolve this by installing the current Java 6 update, which is 31.

Use the link Gremlinzz provided.  I have been recommending that for years.  If the text still refers to update 30, just make corrections to the C&P commands appropriately.  

BUT, do those who use the lab have their own login accounts?  If so, you might want to put the sym link to the plugin in a spot where everyone can use it rather than doing it by user as the tutorial says.

---

### Post by Cavsfan on 2012-02-16
> **QIII said:**
> First, let's see if we can resolve this by installing the current Java 6 update, which is 31.

Use the link Gremlinzz provided.  I have been recommending that for years.

BUT, do those who use the lab have their own login accounts?  If so, you might want to put the sym link to the plugin in a spot where everyone can use it rather than doing it by user as the tutorial says.

You are right, it is a great link. There are links in my sig to check the version and download the update if you do not have 6.31 installed.
Download the ".bin" file and not the ".rpm' file.

The green link is the same as **Gremlinzzz** posted but, it is all ready to go with version 31.
So it is just a matter of copying and pasting. For 32 bit machines the instructions are on the left a ways down and for 64 bit machines the instructions are on the right.
It says to remove the old version first. If you just follow the instructions, you will be fine.

[[color=blue]_Java version 6 update 31 is now available_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1926061)

---

### Post by Cavsfan on 2012-02-16
I noticed that 6.21 was what was in the repositories.
This way you will have to manually update it but, it is best to have the most current version IMO.
I never have any problems with it.

---

### Post by Gremlinzzz on 2012-02-16
the current Java 6 update, which is 31.thanks for the info:popcorn:

---

