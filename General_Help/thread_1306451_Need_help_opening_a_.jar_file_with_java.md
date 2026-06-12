---
title: "Need help opening a .jar file with java"
date: 2009-10-30
forum: General Help
---

### Post by HappyFeet on 2009-10-30
I have a javascipt file I need to open with java. What is the path I need for this? Example: /usr/bin/java  /usr/lib/java

Thanks.

---

### Post by issih on 2009-10-30
A .jar is not a javascript file, java and javascript are not the same thing.

That being said, assuming you have a .jar file, and it is one that has been formulated properly then it should be simply:

```
java -jar filename.jar
```

to launch it.

Be aware though that whilst jar files can be set up to be excecuted like this, they don't HAVE to be, a jar file is essentially just a compressed archive, which contains other files. If the archive contains all the .class files and any resources necessary to run an application and also contains a manifest file that tells the java program how to run it, then the above command will work...if not then you will need to tell us a bit more info

Hope that helps

---

### Post by HappyFeet on 2009-10-30
Thanks for the reply. I'm using kubuntu now, but in the past with gnome, I could just right click>properties>open with>java. I do not have that option in kde. (actually I did, but I accidentally removed java from the list) I need to know the path to the executable java file.

I know I can launch it from the terminal, but I just want to click it and have java open it.

---

### Post by HappyFeet on 2009-10-30
Anyone?

---

### Post by issih on 2009-10-31
I don't really understand the question....generally you do not need the full path to a properly installed executable file.

The system maintains a PATH environment variable which lists all the directories to search for for the executable you want.

This is why regardless of the directory you are in you can type "firefox" and firefox will launch. The system knows the likely locations to look in, and finds it for you.

To this end you should be able to just use "java" on its own with no path.

However, I haven't used kde in anger for a few years now, so perhaps desktop launchers require a full path in that DE.

If you really need to know the full path try using locate to find it

```
locate java
```

Alternatively go to synaptic package manager, navigate to the installed java package, select it and click properties, then click the installed files tab.

Hope that helps

---

### Post by -=Stefan=- on 2009-10-31
> **HappyFeet said:**
> Thanks for the reply. I'm using kubuntu now, but in the past with gnome, I could just right click>properties>open with>java. I do not have that option in kde. (actually I did, but I accidentally removed java from the list) I need to know the path to the executable java file.

I know I can launch it from the terminal, but I just want to click it and have java open it.

Right click on a *.jar file -> Properties -> Edit File Type (tool symbol on the right) -> add -> "java -jar" -> enter -> ok -> ok

The next time you click on a *.jar, the file will be opened with "java -jar"!

---

