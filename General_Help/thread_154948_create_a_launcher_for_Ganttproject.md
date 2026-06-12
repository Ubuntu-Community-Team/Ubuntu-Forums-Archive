---
title: "create a launcher for Ganttproject"
date: 2006-04-04
forum: General Help
---

### Post by damu on 2006-04-04
I decided to use Ganttproject for project management.
I dowloaded and uncompressed the file.
To launch it, I have to double click the file named Ganttproject.sh in the Gantproject folder.
I created a launcher with the Applications menu Editor (Applications/System Tools/  Applications menu Editor).
In the command line, I put > /home/dominique/ganttproject-2.0/ganttproject.sh

The launcher doesn't work :-k 

Any idea why?

---

### Post by RikoW on 2006-04-04
Most likely, the ganttproject.sh script does not find your java installation when started via a launcher.

set the JAVA_HOME variable to the beginning of the script. My java is installed in /opt/java:

```
#!/bin/sh

JAVA_HOME=/opt/java
GP_HOME=/opt/java/Applications/ganttproject

LOCAL_CLASSPATH=$GP_HOME/eclipsito.jar

CONFIGURATION_FILE=$GP_HOME/ganttproject-eclipsito-config.xml
BOOT_CLASS=org.bardsoftware.eclipsito.Boot

if [ -z $JAVA_HOME ]; then
  JAVA_COMMAND=`which java`
  if [ "$?" = "1" ]; then
    echo "No executable java found. Please set JAVA_HOME variable";
    exit;
  fi
else
  JAVA_COMMAND=$JAVA_HOME/bin/java
fi
if [ ! -x $JAVA_COMMAND ]; then
  echo "$JAVA_COMMAND is not executable. Please check the permissions."
  exit
fi
$JAVA_COMMAND -Xmx256m -classpath $CLASSPATH:$LOCAL_CLASSPATH $BOOT_CLASS $CONFIGURATION_FILE $*
```

Your GP_HOME variable would read:
```

GP_HOME=/home/dominique/ganttproject-2.0/
```

Good luck,

               Riko

---

### Post by pauldinu on 2008-05-05
can someone help me create a java laucher for hattrick organizer? the file name is ho.sh and it is located in /media/GAMES/HO/HO.sh. please be a bit more explicit cuz i am a linux noob :confused:... thnx alot

---

