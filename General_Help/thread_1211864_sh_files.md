---
title: "sh files?"
date: 2009-07-13
forum: General Help
---

### Post by Colo2 on 2009-07-13
I tried this and it didn't work. I wanted to have a .sh file with terminal commands in it which I can just execute whenever, adding terminal commands in a .sh file does not execute and run the commands :( Is there any way around this? I just wanted a .cmd equivilant :P

---

### Post by itsjareds on 2009-07-13
Make sure you include this line at the top:
```
#!/bin/sh
```

And then make it executable by typing this in the terminal, not your script:
```
chmod 777 [FILENAME].sh
```

Then you can run the script by either double-clicking it or going to the terminal and cd'ing to your directory, then typing:
```
./[FILENAME].sh
```

---

### Post by sanemanmad on 2009-07-13
or ```
chmod +x filename
```

---

### Post by Colo2 on 2009-07-13
Thanks guys :D Great help

---

### Post by geirha on 2009-07-13
> **itsjareds said:**
> 
And then make it executable by typing this in the terminal, not your script:
```
chmod 777 [FILENAME].sh
```


chmod 777 is really bad advice. Use "chmod +x file.sh" to only add the execute permission, don't make the file writable to the world.

---

