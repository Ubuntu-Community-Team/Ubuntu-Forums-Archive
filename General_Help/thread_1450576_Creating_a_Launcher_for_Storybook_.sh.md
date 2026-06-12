---
title: "Creating a Launcher for Storybook .sh"
date: 2010-04-09
forum: General Help
---

### Post by Tindytim on 2010-04-09
So I recently downloaded Storybook, and using the default storybook.sh from the terminal, or from nautilus works fine launching the application. The command being ./storybook.sh. I have the file set to allow executing the file as a program.

The various combinations I've tried in the launcher include:
```
/home/tim/storybook/storybook.sh
sh /home/tim/storybook/storybook.sh
sh /home/tim/storybook/storybook
```

None of which worked, I then viewed the contents of the file which were:
```
#!/bin/bash

echo "starting ..."
java -Xmx256m -jar lib/storybook.jar
echo "done."
```
So then I tried:
```
java -Xmx256m -jar /home/tim/storybook/lib/storybook.jar
```
which output:
```
2010-04-09 07:09:12,249 INFO  [AWT-EventQueue-0] util.PrefManager (?:?) - connect to: jdbc:h2:/home/tim/.storybook/internal;PAGE_STORE=TRUE
2010-04-09 07:09:12,921 INFO  [AWT-EventQueue-0] util.PrefManager (?:?) - init db, databaseName=/home/tim/.storybook/internal
2010-04-09 07:09:12,923 DEBUG [AWT-EventQueue-0] model.PreferencePeer (?:?) - createTable: create table preference
java.io.FileNotFoundException: configuration.xml (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at ch.intertec.storybook.config.SettingManager.init(Unknown Source)
	at ch.intertec.storybook.config.SettingManager.<init>(Unknown Source)
	at ch.intertec.storybook.config.SettingManager.getInstance(Unknown Source)
	at ch.intertec.storybook.StorybookApp.init(Unknown Source)
	at ch.intertec.storybook.StorybookApp.access$000(Unknown Source)
	at ch.intertec.storybook.StorybookApp$1.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
2010-04-09 07:09:13,002 DEBUG [AWT-EventQueue-0] config.SettingManager (?:?) - settings read from configuration.xml
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at ch.intertec.storybook.config.SettingManager.log(Unknown Source)
	at ch.intertec.storybook.StorybookApp.init(Unknown Source)
	at ch.intertec.storybook.StorybookApp.access$000(Unknown Source)
	at ch.intertec.storybook.StorybookApp$1.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

```
Which didn't launch the application. I've tried some shell scripts, but I'm not well versed in writing them, so any help would be much appreciated.

---

### Post by pj_kare on 2010-04-09
Don't use storybook myself, and don't really know what it is, but I found this:

[http://ubuntuforums.org/showthread.php?p=8220896](http://ubuntuforums.org/showthread.php?p=8220896)

Hope it is of some help.:)

---

### Post by Tindytim on 2010-04-09
Wow, I spent all this time searching for how to create an launcher for a .sh I forgot to search for storybook, THANKS!

---

