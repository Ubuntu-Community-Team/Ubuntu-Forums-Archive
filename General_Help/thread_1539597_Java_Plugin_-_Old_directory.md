---
title: "Java Plugin - Old directory?"
date: 2010-07-26
forum: General Help
---

### Post by pithdillinja on 2010-07-26
Hello all. I am trying to install the ALEKS plugin in firefox 3.6.7. ALEKS is a math education suite type thing, and I am using it to get into college classes.

In order for the ALEKS plugin to work, I need to things: Java and their plugin. ALEKS provides a linux plugin - [http://www.aleks.com/downloads/linux_jvm](http://www.aleks.com/downloads/linux_jvm) - but from the description, it looks like it hasn't been updated for quite a while (since the days of netscape I suppose.)

I contacted them and asked about the situation. They gave me the above link and told me they didn't give support for the linux plugin, but the page has instructions so I figured maybe the geniuses at ubuntuforums can possibly get it working with a little elbow grease.

Now, on the driver download page it says this:

To download manually the plug-in on Linux for Netscape 7.1+,  or Firefox 1.0+, or Mozilla 1.6+, you will have to download the ALEKS  package file and save it on your computer in the **"Java VM lib/ext"** directory. For instance, with the Sun Java VM version 1.4.1, this directory is usually: 
**/usr/java/j2re1.4.1/lib/ext/** 
or 
**/usr/local/j2re1.4.1_02/lib/ext/** 

I tried cd'ing to those directories but they don't exist. My main question is, what is the equivalent for the default java installation that comes with ubuntu?

---

### Post by pithdillinja on 2010-07-26
I would also like to point out that just now, I looked at the java process while it was running and I looked at the files it opened/used. Here were a couple directories:
- /usr/lib/jvm/java-6-openjdk/jre/lib/
- /usr/share/java/
- /home/captain/.icedteaplugin/


- none of these worked though.

---

### Post by luigi_mb on 2010-07-26
> **pithdillinja said:**
> I would also like to point out that just now, I looked at the java process while it was running and I looked at the files it opened/used. Here were a couple directories:
- /usr/lib/jvm/java-6-openjdk/jre/lib/
- /usr/share/java/
- /home/captain/.icedteaplugin/

- none of these worked though.

I think that, using Synaptic, you should uninstall all icedtea and openjdk components, and install sun-java*. The directory you are looking for will then be 

/usr/lib/jvm/java-6-sun-1.6.0.20/ext

or

/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/ext


/luigi

---

### Post by pithdillinja on 2010-07-26
Holy crap - it worked. I read other posts and I had removed openjdk already, but I didn't think getting rid of icedtea too would work. Thank you luigi!

---

### Post by hectoralex on 2010-09-06
I tried these instructions with now joy...  Found found the following thread and it worked like a charm!

[http://ohioloco.ubuntuforums.org/showthread.php?p=9815343#post9815343](http://ohioloco.ubuntuforums.org/showthread.php?p=9815343#post9815343)

):P

---

