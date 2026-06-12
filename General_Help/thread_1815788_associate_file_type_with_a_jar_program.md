---
title: "associate file type with a jar program"
date: 2011-07-31
forum: General Help
---

### Post by poikiloid on 2011-07-31
any way to make a certain file extension (.etxt) open with a certain jar application (enotes.jar) that uses files with that file extension?

i tried (for the custom open command on a .etxt file):

```
java -jar /home/me/Programs/enotes.jar "%1" %*
```

which was proposed (for windows) here: [http://www.thatsjava.com/java-newer/8377/](http://www.thatsjava.com/java-newer/8377/)

but it doesn't work when adapted to linux...

---

### Post by varunendra on 2011-08-01
Try this:
right-click the** file > **click **properties > **goto **'Open with'** tab** > **select (or browse and add) **desired application**.

---

### Post by poikiloid on 2011-08-01
That doesn't work, I believe because a jar file is just a container, not an executable itself. A jar file needs to be run by the java executable, so I had hoped the .etxt could be passed as a parameter after the jar had been invoked in java, in the custom open command above, but it doesn't seem to work either...

---

