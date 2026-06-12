---
title: "frostwire on 9.10"
date: 2009-11-01
forum: General Help
---

### Post by milkweed701 on 2009-11-01
just upgraded to 9.10 - finished very early this morning. frostwire wont open
 - upon starting frostwire, instead of seeing the "cool eye" i get this message:
> FrostWire version 4.17
Java version 1.6.0_16 from Sun Microsystems Inc.
Linux v. 2.6.31-14-generic on i386
Free/total memory: 47650856/48300032

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.limewire.util.VersionUtils
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 6 more

STARTUP ERROR!please help me! willing to try anything...
 - already tried d/l-ing the .deb from the site, uninstalls, re-installs, installing from synaptic...

---

### Post by Crafty Kisses on 2009-11-01
From what I remember there are some problems with Frostwire as a deb package not sure why. Try downloading the RPM from Frostwire's website and then use Alien to convert the package back to a deb. So grab the RPM right [here]("http://www.frostwire.com/download/?os=redhat&"). Now that you have that RPM you need to install Alien and convert the package:
```
apt-get install alien
alien -i frostwire*
```
Then Frostwire should work, now if it doesn't let me know and I will try to help you further, I also recall there are some Java problems with Frostwire, but let's see if this works first before I help you any further.

---

### Post by milkweed701 on 2009-11-01
tried and nothing..... sorry for the late response, fiancee had to play with cafe world on facebook

---

### Post by Furry_Fighter_20x66 on 2009-11-01
I had the same problem as well. Somethings wrong with the packages. A person over on the Frostwire forums posted his fix and it worked for me.

-remove the old version of frostwire. 
(Remove the /usr/lib/frostwire directory if it still exists as well)
-Download the tarball from frostwire.
-untar the tarball
-take the directory and rename it from frostwire.noarch or whatever it is called to simply frostwire
-move it to /usr/lib/
then you can launch it using the run script in the directory. Set up some links in your menu and whatever else you need to do for permissions and it seems to be good to go.

Of course make sure you're using Sun's Java. Set it up using instructions from here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Hope this helps get you going as well.

---

### Post by milkweed701 on 2009-11-02
awesome!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

thank you, all of you who tried, im sure you meant well.
thank you furry fighter - its running well...
and, last but not least, thank you souta95, i know you didnt comment in this thread, but darn it, friend, after we tried all we could, you sent me to this site...

thanks again guys!!!

---

### Post by milkweed701 on 2009-11-02
erm... sorry... noob here.. how do i label this problem as 'solved'?


feel-like-an-idiot-ly, 
me

---

### Post by rockstarrem on 2009-11-02
At the top of the thread - Thread Tools > Mark As Solved.

---

### Post by milkweed701 on 2009-11-02
thank you rockstarrem

---

### Post by cowboy7305 on 2009-11-04
I know this is solved 
just a big thank you to crafty kisses, did what you said worked just great many thanks 
i can now stop banging my head on the door

---

### Post by milkweed701 on 2009-11-04
alright, now i have a question... why did crafty kisses suggestion work for the person's post just above this one (sorry, dont remember the name...) not work for me, but the other one did?

---

### Post by cowboy7305 on 2009-11-04
Did you put sudo in front of the codes  i had to do that before thy would work

---

### Post by milkweed701 on 2009-11-05
@cowboy7305 yessir, i most certainly did

---

