---
title: "Java plugin not loading"
date: 2010-11-29
forum: General Help
---

### Post by eival on 2010-11-29
i just upgraded jave thru the repos to 6.22 and i see the latest java plugin installed in firefox 1.6.0_22 yet when i test it on java.com it takes forever to load an when it does i just see a gray box

before i upgraded it would only take a second for it to give me my results, so i dont know whats going on.

---

### Post by GregBrannon on 2010-11-29
Type

```
> java -version
```

at the terminal prompt and report results.

---

### Post by eival on 2010-11-29
> **GregBrannon said:**
> Type

```
> java -version
```

at the terminal prompt and report results.

first it says bash: java: Permission denied

then i added sudo and it says -version: command not found

EDIT- nvm, that greater than sign seems to be unnessisary idk why you included it.

heres my results

java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)


and heres a screencap of the test page plus my plugin showing i have the lastest version

[http://img89.imageshack.us/img89/6766/screenshothyy.jpg](http://img89.imageshack.us/img89/6766/screenshothyy.jpg)

---

### Post by lykeion on 2010-11-30
> **eival said:**
> 
EDIT- nvm, that greater than sign seems to be unnessisary idk why you included it.
The greater-than-sign is there as a [command prompt]("http://en.wikipedia.org/wiki/Command-line_interface#Command_prompt"), i.e. to show you that the command should be run in a [terminal]("http://en.wikipedia.org/wiki/Terminal_emulator"). 
It should not be included in the command (as you've noticed).

Do you have any other problem with the Java plugin other than the Java test site takes a long time to load? 
If not it's more likely a browser issue. Try to clear browser cache. 
You can also clear the Java cache: 
System > Preferences > Sun Java 6 Plugin Control Panel
Temporary Internet Files > Settings... > Delete Files...

---

### Post by eival on 2010-12-01
> **lykeion said:**
> 
Do you have any other problem with the Java plugin other than the Java test site takes a long time to load? 
If not it's more likely a browser issue. Try to clear browser cache. 
You can also clear the Java cache: 
System > Preferences > Sun Java 6 Plugin Control Panel
Temporary Internet Files > Settings... > Delete Files...

yeah it doesnt load at all, which is what this thread was about,
i ran the test with the defual 6.18 plugin an the results came back instantly telling me to upgrade, i tried using the bin file but thats a pain in the butt, so i just upgraded thru the repositories, and uninstalled the 6.18.

now the test takes for ever to respond an when it does, as the screencap above shows its just a blank gray box which i assume is suppose to be the applet.

i checked the java control panel and theres no files at all to be deleted, so thats not the issue.

---

### Post by runeh76 on 2010-12-01
> **eival said:**
> yeah it doesnt load at all, which is what this thread was about,
i ran the test with the defual 6.18 plugin an the results came back instantly telling me to upgrade, i tried using the bin file but thats a pain in the butt, so i just upgraded thru the repositories, and uninstalled the 6.18.

now the test takes for ever to respond an when it does, as the screencap above shows its just a blank gray box which i assume is suppose to be the applet.

i checked the java control panel and theres no files at all to be deleted, so thats not the issue.


If u looking around earlier threads, u find solution.

---

### Post by lykeion on 2010-12-01
> **runeh76 said:**
> If u looking around earlier threads, u find solution.That's rather cryptical...

Have you tried to remove the IcedTea Java browser plugin. It may conflict with the Sun Java browser plugin. In a terminal enter this: ```
sudo apt-get remove icedtea6-plugin
```
Then restart the browser and test Java again: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by runeh76 on 2010-12-01
> **lykeion said:**
> That's rather cryptical...

Have you tried to remove the IcedTea Java browser plugin. It may conflict with the Sun Java browser plugin. In a terminal enter this: ```
sudo apt-get remove icedtea6-plugin
```Then restart the browser and test Java again: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Sry mate but earlier threads are full solved things. Peoples are just lazy to look around.

Cheers

---

