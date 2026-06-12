---
title: "ubuntu System policy prevents shutting down"
date: 2010-05-25
forum: General Help
---

### Post by gogic on 2010-05-25
"I get message ubuntu System policy prevents shutting down" when i try to turn off ubuntu ( i get similar message when i try to restart too )

Am the only user 
I have installed hsqldb-server ( and mb he has something to do with it )

Can u help in removing this message ?

---

### Post by arrange on 2010-05-25
What Ubuntu are you using? I don't see this message in my lucid *polkit* files. Could you post the output of```
pkaction --verbose | grep -B2 -A6 shutting
```

---

### Post by gogic on 2010-05-25
am using 10.04

I dont get any output from that command

---

### Post by arrange on 2010-05-25
So is it literally "shutting down"? Could you post a screenshot?

---

### Post by bodhi.zazen on 2010-05-25
does this thread help ?

[http://ubuntuforums.org/showthread.php?t=1328592](http://ubuntuforums.org/showthread.php?t=1328592)

[http://www.len.ro/2009/11/karmic-various-tricks/](http://www.len.ro/2009/11/karmic-various-tricks/)

---

### Post by gogic on 2010-05-25
Yes , i have the same problems like people from both threads but i as i said am an only user to this pc ( only login option is mine too ) , and i didn't use any fancy server commands from other pc or from my

I can't make a screanshot cos there are 2 options one is cancel ( that will logout me and i lose screanshot ) and authenticate ( that will restart my pc - i need to write my password)

In first thread there is command  
top -b -n 1|tail -n +8|awk '{print $2}'|sort|uniq

and when i run it i get :
avahi
daemon
gdm
haldaemo
hsqldb <<-- hsqldb ? server
messageb
gogic <<-- my user
mysql <<-- mysql ? server
root
rtkit
syslog
www-data


Ubuntu is using multi users [http://ubuntuforums.org/showthread.php?t=696420](http://ubuntuforums.org/showthread.php?t=696420) ?

---

