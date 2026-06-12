---
title: "startup applications"
date: 2010-05-26
forum: General Help
---

### Post by gogreenpower on 2010-05-26
i have just upgraded to 10.04 from 9.10 and i used to have a java program i added to system/preferences/startup applications and it worked fine in 9.10. but now i cant get it to work in 10.04. 

i have deleted the entry and added it again but still no luck. all the other default apps in the startup applications start and work fine. and i can start the app manually and it works fine. 

any ideas?

---

### Post by meho_r on 2010-05-26
I tested this with JabRef, which is a Java applications. Here's what I did:

1. put JabRef-2.6.jar file in **~/bin** folder,

2. checked that "Allow executing file as a program" for *JabRef-2.6.jar* file is activated (Right click > Properties > Permissions),

3. created an entry in "StartUp Applications" with this entry in "Command" field:
```

java -jar /home/mehor/bin/JabRef-2.6.jar

```
After that I logged out, then again logged in and JabRef started.

---

