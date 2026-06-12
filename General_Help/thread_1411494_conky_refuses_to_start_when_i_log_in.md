---
title: "conky refuses to start when i log in"
date: 2010-02-20
forum: General Help
---

### Post by chrismitt2002 on 2010-02-20
as the title states conky refuses to start when i log in  here is a sample of my start up config 
#!/bin/bash
sleep 20 && conky this works fine on my print server box running ubuntu 810 
been doing it this way for a while im now runnuing 910 on another pc (much newer then my print-server and i cant get conky to run when i log in and have no clue what im doing wrong and heres the funny thing about it on my print-server i dont even have a start up script just conky in the command line box in start up

---

### Post by switch10 on 2010-02-20
I am having the same issue...

---

### Post by stinkeye on 2010-02-20
If your using compiz you can try this method.
Ignore the first part about wmctrl.
[_**[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8376643&postcount=9[/COLOR]**_]("http://ubuntuforums.org/showpost.php?p=8376643&postcount=9")

---

### Post by switch10 on 2010-02-20
Thanks!!

It works great now.

Copy and paste this into gedit...


```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 conky >/dev/null 2>&1 &
                
                
		done="true";
	else
		echo "CONKY IS WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0 
```

save it in your /home folder as conky

then do this to make it executable, 

```
 chmod u+x conky 
```

then go to System>Prefs>startup aplications, and add conky as /home/username/conky

---

