---
title: "Help!"
date: 2012-05-11
forum: General Help
---

### Post by spartan godd on 2012-05-11
Okay, im trying to make a .jar file executable in the terminal. I use "chmod +x filename.jar" but when I drag my file into the terminal to get its location, then press enter, it says that there is "no such file or directory". I'm not sure what I'm doing wrong, and I am a newbie at Linux, thanks for the help.

---

### Post by codemaniac on 2012-05-11
Have you tried to find out the location of your jar file , by using find , locate ?

---

### Post by Zvlwab on 2012-05-11
I'm guessing you tried running
```
/path/to/file
```

You can run a jar file by using
```
java -jar /path/to/file
```

---

