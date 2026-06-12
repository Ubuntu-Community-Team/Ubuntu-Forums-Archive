---
title: "Terminal and Ping?"
date: 2009-06-28
forum: General Help
---

### Post by agavril on 2009-06-28
Hello, Ubuntu World, I am having some problems with terminal, mainly with the ping command. First thing is that for some reason when i try to ping something, it automatically starts to when you write in windows CMD it goes like ex. C:\documents and settings\user.compname> ping 70.70.168.152 -t -l 65500. and when I just want to ping my own server it tries to automatically so a Dos attack. which is really grinding my gears :P   :confused:. Please help!!!!

Cheers, 
    Arthur

---

### Post by DeMus on 2009-06-28
> **agavril said:**
> Hello, Ubuntu World, I am having some problems with terminal, mainly with the ping command. First thing is that for some reason when i try to ping something, it automatically starts to when you write in windows CMD it goes like ex. C:\documents and settings\user.compname> ping 70.70.168.152 -t -l 65500. and when I just want to ping my own server it tries to automatically so a Dos attack. which is really grinding my gears :P   :confused:. Please help!!!!

Cheers, 
    Arthur

Could you please be more clear about your problem? Please tell exactly what you do and what happens then? Do you do this in Ubuntu or in Windows? Your story is not clear about this.

---

### Post by agavril on 2009-06-28
> **DeMus said:**
> Could you please be more clear about your problem? Please tell exactly what you do and what happens then? Do you do this in Ubuntu or in Windows? Your story is not clear about this.

I'm using ubuntu and whenever i try to ping my own server it just continues on and on and on for over 3 or 4 hours, (found out because was rushing to leave) and my server crashed.

---

### Post by onomou on 2009-06-28
Ping in Ubuntu keeps going until you tell it to stop (press Ctrl+c), unless you specify to only do a certain number of pings. Use ```
ping -c (count) (destination)
``` to do only a certain number of pings. For results like in Windows, do ```
ping -c 4 (destination)
```

---

### Post by agavril on 2009-06-28
THANK YOU SO MUCH! i was so confused! :D :D :D :D

---

### Post by rushikesh988 on 2009-06-28
we can do this from network tools too

---

### Post by mhgsys on 2009-06-28
You could also stop the ping command by pressing Ctrl + C

but ping -c will do the trick for you.

---

