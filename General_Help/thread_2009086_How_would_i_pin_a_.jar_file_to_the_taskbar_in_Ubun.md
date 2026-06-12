---
title: "How would i pin a .jar file to the taskbar in Ubuntu"
date: 2012-06-23
forum: General Help
---

### Post by ubuntoneedhelp303 on 2012-06-23
How would I make it so that I can run a .jar file from the  task bar on the side in Ubuntu As it is I cannot drop a .jar file onto  it. 
  How would I create something that I could pin to the Task bar that  would link into running the .jar. Just in case you need to know I am  trying to put minecraft onto the task bar and I cannot seem to correctly  make a desktop file to link to it. Help would be nice :D:o:D

---

### Post by ubuntoneedhelp303 on 2012-06-24
Bump.

---

### Post by stinkeye on 2012-06-24
Make yourself a **minecraft.desktop** file and place in **~/.local/share/applications**
then drag to the launcher.

eg 
I have a launcher for a java app called FFgenie
My **~/.local/share/FFgenie.desktop** file.
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=java -jar '/home/glen/Football/ffgenie/dist/FFGenie.jar'
Name=FFgenie
Icon=/home/glen/Pictures/Genie2.png
```

---

### Post by ubuntoneedhelp303 on 2012-07-07
Bump. I didn't keep track with this post but i tried the method above and i get this:  [COLOR=DarkRed]**There was an error launching the application. **[COLOR=Black]If anyone else can help please?[/COLOR][/COLOR] :KS

---

### Post by ubuntoneedhelp303 on 2012-07-08
Bump.

---

### Post by ubuntoneedhelp303 on 2012-07-08
Come on i thought this would be an easy question still no help....

---

### Post by ubuntoneedhelp303 on 2012-07-08
I kept trying the 1st answer and i figured out how to do it thanks!!!! :KS

---

