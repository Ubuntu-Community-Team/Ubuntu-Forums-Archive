---
title: "Start one shell script from inside another?"
date: 2009-09-05
forum: General Help
---

### Post by qwerty123abc on 2009-09-05
Is there a simple shell script that starts another shell script and opens and closes it in X amount of seconds?

Ive found a windows batch one that does what i need..

>            :start
                  set time=30
                  start test.bat
           :loop
                  cls
                  IF %time% GTR 0 (
                   set /a time=%time% - 1
                    set /a min=%time%/60
                     echo Next Restart In %time% Seconds.
                    echo   %time% Seconds is %min% Minutes.
                   ping 127.0.0.1 -n 2 > NUL
                  goto loop
                  ) 
           taskkill /f /im java.exe
          cls
         goto start

Could someone write or find a shell script that does somthing like that batch?

Thanks :D

---

### Post by falconindy on 2009-09-05
I just remembered why I hate Windows batch scripting, if you can even call it scripting...

```
#! /bin/bash

while [ 1 ]; do
    /path/to/other/script
    sleep 30
    pkill -9 script
done
```
You just need to replace the path of the script in the first line of the loop and then the name of the script alone in the third line.

edit: I'm afraid to ask, but my curiosity is getting the best of me. Rarely do you ever need a script like this. What are you trying to do?

---

### Post by qwerty123abc on 2009-09-05
I get permission denied even when trying to run as root.

Also
> echo Next Restart In %time% Seconds.
                    echo   %time% Seconds is %min% Minutes.

To restart somthing lol.

---

### Post by qwerty123abc on 2009-09-05
edit: not fixed... i keep getting "Permission Denied"

---

### Post by qwerty123abc on 2009-09-06
need help.

---

### Post by DaithiF on 2009-09-06
have you made the script executable?
```
chmod +x yourscript.sh
```

---

