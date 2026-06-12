---
title: "launcher for .jar"
date: 2012-05-18
forum: General Help
---

### Post by ottosykora on 2012-05-18
I need to make a launche button for a jar program in the menu (classic 12.04)

I managed to have a shortcut to it on the desktop, but would like to have it in the menu. But when I create an entry to the menu, it does not work.

I think I could do with some .sh script, in fact I have one , but even this one does not work.

#!/bin/sh
java -jar ./PortablePGP.jar


how to do it better? so it works?

---

### Post by Cheesemill on 2012-05-18
Try using the full path to the .jar file. For example:
```
#!/bin/sh
java -jar /home/user/PortablePGP.jar
```

---

### Post by ottosykora on 2012-05-18
just tried to put in full correct path, but nothing happends, and yes I marked it executable

it must  be something with the java part

---

### Post by Cheesemill on 2012-05-18
Try with the full path to java as well then:
```
#!/bin/sh
/usr/bin/java -jar /home/user/PortablePGP.jar
```

---

### Post by ottosykora on 2012-05-18
bingo, it is ok now, thanks

---

