---
title: "Ubuntu .bat equivalent?"
date: 2009-12-05
forum: General Help
---

### Post by Skyline969 on 2009-12-05
Ok, I have an executable .jar file, and what I want to do is create a Linux equivalent to a batch file so I can just double-click the file to run the executable jar. The only command I would need to run is

java -jar myjarname.jar

And then place it in the same folder as the jar file, I would assume. But what do I do to make the file execute when I double-click it? I made a .txt file and just had that command in there, but it opens in gedit.

Thanks in advance.

---

### Post by JBAlaska on 2009-12-05
You can simply do it as so:
* Right click on any .jar file
* Select properties
* Navigate to the open with tab in the properties window
* Check off "Sun java X.x.x Runtime" (without the quotes) then hit OK

Replace X.x.x with your version of the runtime.

You can create a shell script that will allow you to set Java settings (mem usage, etc). But the above should do what you want.

---

### Post by NoaHall on 2009-12-05
Here -
```

#! /bin/bash
java -jar myjarname.jar

```
Save that in a file without a extension(extensions don't matter on Linux). Then open a terminal, and run the command
```
chmod +x /filename/
```

---

### Post by Skyline969 on 2009-12-05
> **JBAlaska said:**
> You can simply do it as so:
* Right click on any .jar file
* Select properties
* Navigate to the open with tab in the properties window
* Check off "Sun java X.x.x Runtime" (without the quotes) then hit OK

Replace X.x.x with your version of the runtime.

You can create a shell script that will allow you to set Java settings (mem usage, etc). But the above should do what you want.

/facepalm
Yup, it's that simple. No need for a shell script at all. I'm too used to wrapping jar files for Windows (or writing a batch file) so I can run them without opening the command prompt. Thanks JBAlaska!

---

