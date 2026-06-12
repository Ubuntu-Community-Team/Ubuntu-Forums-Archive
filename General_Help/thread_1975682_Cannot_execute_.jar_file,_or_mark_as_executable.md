---
title: "Cannot execute .jar file, or mark as executable"
date: 2012-05-07
forum: General Help
---

### Post by SerFaren on 2012-05-07
So, I recently downloaded minecraft from here: [http://www.minecraft.net/download](http://www.minecraft.net/download)
and I have done everything there is to do. I have Java, OpenJDK Java Runtime 6 {And 7}, and I can't seem to get it to become executable from OpenJDK Java Runtime 6. 

I tried to do this in the terminal, but it refuses to work: 
```
chmod +x ~/desktop/minecraft.jar
```I have no idea what to do!
I open up the preferences and I cannot mark it as executable, seeing as it's not an option. 

Please help! Thanks<3

EDIT: I am running on 11.10, if that helps.

---

### Post by Toz on 2012-05-07
Hello and welcome to the forums. 

Try opening a terminal window and running the following commands:
```
cd ~/Desktop
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```

---

