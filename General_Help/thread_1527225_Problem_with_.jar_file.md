---
title: "Problem with .jar file"
date: 2010-07-09
forum: General Help
---

### Post by qogima1024 on 2010-07-09
I am trying to install WebOS Quick Install via a .jar file. When i execute it via OpenJDK Java 6 Runtime, it says that it needs WebOS Doctor in order to run and asks if i would like to download it. When i confirm, nothing happends.  I ran this script in the terminal:

java -jar [filename_of_the_jar.jar]

and got this as the output:


	at java.beans.Encoder.writeExpression(Encoder.java:304)
	at java.beans.XMLEncoder.writeExpression(XMLEncoder.java:389)
	at java.beans.DefaultPersistenceDelegate.doProperty(DefaultPersistenceDelegate.java:229)
	at java.beans.DefaultPersistenceDelegate.initBean(DefaultPersistenceDelegate.java:264)
	at java.beans.DefaultPersistenceDelegate.initialize(DefaultPersistenceDelegate.java:408)
	at java.beans.PersistenceDelegate.writeObject(PersistenceDelegate.java:116)
	at java.beans.Encoder.writeObject(Encoder.java:74)
	at java.beans.XMLEncoder.writeObject(XMLEncoder.java:274)

...repeating over and over taking up the whole terminal.

Any help would be much appreciated.

---

### Post by JustinAlf on 2010-08-04
I have the same problem, please help!

---

### Post by JustinAlf on 2010-08-04
Fixed it, had an opensource version of java installed.  Installed form sun and then it worked.

---

