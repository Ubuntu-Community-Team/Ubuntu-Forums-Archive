---
title: "Creating link to a .java file with parameters"
date: 2010-10-24
forum: General Help
---

### Post by Byroboy on 2010-10-24
I have a Java program (minecraft server) that needs to be run from the command line. 
The code is:
```
java -Xmx512M -Xms512M -jar minecraft_server.jar nogui
```

To make life easy (i've got the java file in a folder on the desktop) I want to have a shortcut (or similar) sitting on the desktop.
I've tried 
```
ln 'java -Xmx512M -Xms512M -jar minecraft_server.jar nogui' ./../minesraftserver
```
with single and double quotes but my unix command line skills are pretty basic and this is obviously incorrect.

Any help is appreciated, I know this is probably quite simple. :)

---

### Post by Vaphell on 2010-10-24
i think ln command doesn't do what you think it does

either way create a script with the name of your choice and place it where you want. don't forget to set it to executable

```

#!/bin/bash
java -Xmx512M -Xms512M -jar minecraft_server.jar nogui

```

or create a launcher on a panel (right-click, add...) and try
sh -c 'java -Xmx512M -Xms512M -jar minecraft_server.jar nogui' (or the script above)
i suspect there can be a problem with .jar location so provide a full path to that file

---

### Post by inameiname on 2010-10-25
That's what I did with a jar application, just put it in the same folder as a super basic shell script which links it. Oh, and I have the folder inside my ~/.gnome2/nautilus-scripts folder so I can easily run the jar application by a right click.

---

