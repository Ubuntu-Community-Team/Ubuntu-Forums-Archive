---
title: "Need to change the working directory of my script."
date: 2011-08-05
forum: General Help
---

### Post by false_chicken on 2011-08-05
I have a script that should start my Minecraft server. The script is a follows:

#!/bin/bash
java -Xincgc -Xmx1G -jar "/home/jamie/Programs/Minecraft Server/craftbukkit-0.0.1-SNAPSHOT.jar"

The script is located in my scripts directory in my home folder and it is in my path. But when I execute the script the server starts writing all the data to my home folder(The directory I am in). How can I tell the script to change its working directory to the server folder? Thanks.

---

### Post by mikewhatever on 2011-08-05
Start the script with cd /server-folder?

---

### Post by false_chicken on 2011-08-05
That worked. Thanks. For some reason I thought it wouldn't. I think I tried something similar in the past and it didn't work.

---

