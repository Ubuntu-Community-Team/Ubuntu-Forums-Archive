---
title: "ubuntu goes on crashing unexpectadly"
date: 2009-09-18
forum: General Help
---

### Post by prakreet on 2009-09-18
I am using ubuntu 9.04. i have also installed the kde environment on my system. My problem is that sometimes ubuntu crashes unexpectedly.. the only way out of the crash is to cut the power to the comp. 

once it happened when i was opening an rmvb file with vlc. another time i was trying to seek a movie in totem when ubuntu crashed. but a funny thing is that i could move my mouse normally and the sound of the movie i was trying to seek was playing normally while the rest of the system crashed. 

i tried the alt-f2 keys to bring up the run terminal but it does not appear. please help me. maybe its a bug.. but could u please suggest any way to get out of the crash...
maybe a nastier way than using alt- f2 and typing xkill....

---

### Post by imhotep59 on 2009-09-18
> **prakreet said:**
> 
i tried the alt-f2 keys 

To run a terminal: ctrl-alt-F1
Then try: top (to see the runing process and identify which is bugging)
Then you can kill the process: kill -9 PID (where PID is the number of the process you want to kill)

---

### Post by rocket16 on 2009-09-18
This is a nice procedure. Additionally, if you do not know the process-name then use "killall -user name" (where name=username). This will return you to the login screen.

---

### Post by 3rdalbum on 2009-09-18
You can kill the X server (and all your graphical programs) by pressing Alt-SysRq(Print Screen)-K. In a couple of seconds you will be back at the login screen.

If you're using Intrepid (Ubuntu 8.10) or earlier, the keyboard combination is Control-Alt-Backspace.

---

### Post by imhotep59 on 2009-09-18
Well, i think the best procedure is: 
- first, to identify the process that caused the bug. That's why i prefer the command ```
top
``` or ```
ps aux | less
```. This help you to understand what is happening (and maybe you will be able to prevent another crash). 
- second, you just have to kill the process which is responsible of the crash and you can return to the graphic session with ctrl-alt-F7. So, you don't need to reboot or relog.

---

### Post by prakreet on 2009-09-29
Thank u guys for ur support. i 'll surely try these when i get another crash.....

---

