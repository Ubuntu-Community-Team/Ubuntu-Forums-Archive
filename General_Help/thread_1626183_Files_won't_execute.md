---
title: "Files won't execute"
date: 2010-11-20
forum: General Help
---

### Post by hantechbl on 2010-11-20
I am having trouble getting files to execute, even though I used chmod 777 on them, I don't know what I did wrong, I use ubuntu server so only the terminal is available to me.

---

### Post by dcstar on 2010-11-20
> **hantechbl said:**
> I am having trouble getting files to execute, even though I used chmod 777 on them, I don't know what I did wrong, I use ubuntu server so only the terminal is available to me.

**Exactly** what?

Please read the link at the end of my sig.

---

### Post by wojox on 2010-11-20
Use 

```
chmod a+x myfile
```

chmod 777 just makes it writeable. :)

---

### Post by dcstar on 2010-11-20
> **wojox said:**
> Use 

```
chmod a+x myfile
```

chmod 777 just makes it writeable. :)

Rubbish, chmod 777 sets the Execute permission (and Read and Write as well) on all groups.

---

### Post by wojox on 2010-11-20
Your right. I was thinking of chmod 666. ;)

---

### Post by endotherm on 2010-11-20
if you are in the folder that contains the script or app, do you add './' in front of your command? 
```

./scriptname
OR
sh ./scriptname

```


what is it you are running? a script? does it have a bangline?
```

#!/bin/bash
or
#!/[FONT=Arial, Helvetica, sans-serif][SIZE=2]usr/bin/**env** **python**[/SIZE][/FONT]

```

---

### Post by hantechbl on 2010-11-20
It has a bangline, i did the chmod a+x and it still won't work, I also did the sh ./server_nogui.sh and it said "sh: Can't open"
It is a simple script, just says to load minecraft_mod.jar with the set parameters, it worked on the hdd, and I copied the files to the Flash and now it doesn't work.

---

### Post by wojox on 2010-11-21
Did you sudo it?

---

