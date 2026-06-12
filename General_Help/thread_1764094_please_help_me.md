---
title: "please help me"
date: 2011-05-21
forum: General Help
---

### Post by kolmad on 2011-05-21
i need to play a runescape private serverand need someone to convert these .bat files to .sh files:

```
@echo off
Title Redemption Client
cd ./Class/
"C:\Program Files (x86)\Java\jre6\bin\java.exe" -Xmx500m -cp . Gui 30 0 lowmem members 32
pause
```

```
@echo off
title Building Files
"C:\Program Files\Java\jdk1.6.0_24\bin\javac.exe" -d ./Class/ Java/*.java Java/sign/*.java
pause
```

tahnks

---

### Post by kolmad on 2011-05-21
bump

---

### Post by kolmad on 2011-05-21
bump! please help!

---

### Post by Mr. Shannon on 2011-05-21
First there is no C drive on Linux so you would first need to convert those paths to Linux paths and not Windows paths.  Also remove the quotes around the paths.  Put # in front of comments and remove the @echo off.  Put all of it in between
```

#!/bin/bash

code goes here...

exit 0

```
and then in a terminal use
```
sudo chmod a+x /path/to/your/script
```

I don't understand the rest of those scripts so if that does not work then you will need someone else's help.

---

### Post by kolmad on 2011-05-22
didnt work :/

---

