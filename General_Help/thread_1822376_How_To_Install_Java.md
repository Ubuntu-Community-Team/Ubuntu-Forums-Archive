---
title: "How To Install Java"
date: 2011-08-10
forum: General Help
---

### Post by carmenat250 on 2011-08-10
Could someone tell me how to install Java on Ubuntu?

On Windows, it's just running an .exe file, but when I went to the Java download page ( [http://www.java.com/en/download/manual.jsp?locale=en](http://www.java.com/en/download/manual.jsp?locale=en) ), the install instructions seem a little involved.

I was hoping there was an easier way to install this.  I am using Google Chrome and I am running the 32-bit version of OS.

---

### Post by zero244 on 2011-08-10
Well I think the easiest way would be to Open the the Ubuntu software center or synaptic and search for Java.
Then install the Java runtime stuff etc.

Should only take a few clicks and your done.

---

### Post by kvaadithya on 2011-08-10
Please try the following:

1. Close all Chrome and Firefox windows.

2. Type the following into a terminal:

```

$ sudo apt-get install sun-java6-plugin   # or whichever version is current in synaptic

```

3. Start Chrome again, and the java plugin should be running. To check this, type "about:plugins" (without the quotes) in the chrome address bar, and it will show a list of all plugins. It should say that the Java plugin is enabled.

4. It takes a little bit more effort to get Firefox to recognize the Java plugin (in case you're also interested in this). For this, open up a terminal and type:

```

$ cd /home/<your username>/.mozilla/plugins   # create the plugins directory if it is not already there
$ ln -s /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnpjp2.so

```

(where 1.6.0.26 is the version of Java installed, replace it with your version if it is different)

That should have Java up and running in firefox (which you can check by typing about:plugins in the Firefox address bar).

---

### Post by carmenat250 on 2011-08-11
Thanks for the suggestions.

I just found the IcedTea plug-in within the Synaptic Packet Manager and that seems to work really well.

---

