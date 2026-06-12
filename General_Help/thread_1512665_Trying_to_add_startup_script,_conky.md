---
title: "Trying to add startup script, conky"
date: 2010-06-18
forum: General Help
---

### Post by localguy on 2010-06-18
Hello,

i'm having problems making or adding a script for conky to start up when i boot up..

i opened up Application then Gedit then copyied
 #!/bin/bash
sleep 10 && conky;

then saved as .conky_start.sh 

i see it in there but its a different looking file, i must be doing something wrong and cant see where?

i even added it to start up applications still no go

---

### Post by Wardje on 2010-06-18
Check the following things:

**a. Is the file executable?**

You can check or change this by right clicking the file in nautilus (CTRL+H to show hidden files), selecting properties -> permissions.
Alternatively, you can use the terminal and issue this command
```
chmod +x .conky_start.sh
```

**b. Does it work if you try executing it yourself?**

Issue ```
./conky_start.sh
``` in a terminal and see if conky shows after 10 seconds.

**c. Does conky actually start on system start up?**

To check this, after start up open a terminal and type
```
ps -e | grep conky
```
If it is running, you'll need to make it sleep for longer before starting.
For example, on my system I use 30 seconds to be on the safe side. This is the contents of my conky startup file:
```
#!/bin/bash
sleep 30
/usr/bin/conky

```

---

### Post by localguy on 2010-06-18
> **Wardje said:**
> Check the following things:

**a. Is the file executable?**

You can check or change this by right clicking the file in nautilus (CTRL+H to show hidden files), selecting properties -> permissions.
Alternatively, you can use the terminal and issue this command
```
chmod +x .conky_start.sh
```**b. Does it work if you try executing it yourself?**

Issue ```
./conky_start.sh
``` in a terminal and see if conky shows after 10 seconds.

**c. Does conky actually start on system start up?**

To check this, after start up open a terminal and type
```
ps -e | grep conky
```If it is running, you'll need to make it sleep for longer before starting.
For example, on my system I use 30 seconds to be on the safe side. This is the contents of my conky startup file:
```
#!/bin/bash
sleep 30
/usr/bin/conky

```

it dont start when i reboot i have to alt-f2 to start it manualy

---

