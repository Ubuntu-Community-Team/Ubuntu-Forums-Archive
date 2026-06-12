---
title: "Cant able to view my log file.."
date: 2010-02-17
forum: General Help
---

### Post by karthick87 on 2010-02-17
I cant able to view my log file..How to view the file?

---

### Post by darolu on 2010-02-17
It's either permissions issue or the file is encrypted. Try opening with gksu, press Atl+F2 and type "gksu gedit /var/log/logkeys.log"; if it fails, means your file is encrypted, refer to your keylogger program's documentation to learn how to open the file.

---

### Post by karthick87 on 2010-02-18
I have opened it with gksu..But this was the output cant able to view anything...

&#28492;&#26471;&#28265;&#8295;&#29811;&#29281;&#25972;&#8292;&#11822;&#2606;&#12810;&#12592;&#11568;&#12848;&#12589;&#8248;&#14640;&#12602;&#14900;&#13108;&#12331;&#13109;‰&#8254;&#19516;&#29763;&#27762;&#29758;&#28007;&#26977;&#15468;&#17228;&#29300;&#15980;&#2560;&#12338;&#12337;&#12333;&#11570;&#14385;&#12320;&#14905;&#13617;&#12346;&#11064;&#13616;&#12339;&#15904;&#2592;&#19466;&#26479;&#26983;&#26478;&#29472;&#28532;&#28784;&#25701;&#24864;&#8308;&#12338;&#12337;&#12333;&#11570;&#14385;&#12320;&#14905;&#13873;&#13626;&#11058;&#13616;&#12339;&#2570;

---

### Post by jobix on 2010-02-18
If you execute this from a terminal:

> file /var/log/logkeys.log

what does it show?

---

### Post by karthick87 on 2010-02-18
karthick@Learners-desktop:~$ file /var/log/logkeys.log 
/var/log/logkeys.log: regular file, no read permission

---

### Post by ethoxyethaan on 2010-02-18
sudo cat /var/log/logkeys.log

---

### Post by jobix on 2010-02-19
> **getyourkarthick said:**
> karthick@Learners-desktop:~$ file /var/log/logkeys.log 
/var/log/logkeys.log: regular file, no read permission

Looks like you don't have read permissions. Use "chmod" to change that and you should be able to read it.

---

### Post by UBVirginia on 2010-05-15
hi,
i think i have a similar problem.. or same? 
have after alof of trouble installed logkeys (i think) but cant find the file /var/log/logkeys.log

$ file /var/log/logkeys.log
/var/log/logkeys.log: ERROR: cannot open `/var/log/logkeys.log' (No such file or directory)

have i not installed the program correctly? or is the file somewhere else?

so now im not that sure if i'm running the program or not?!
there is no such file as /var/log/logkeys.log
and when i type the command 
touch test.log
in the terminal i get
touch: cannot touch `test.log': Permission denied
and when typing
logkeys --start --output test.log
i get: logkeys: Another process already running. Quitting.

confused! thought i had it all sorted by now.. is it not installed correctly ?

but while i'm at it, 
will logkeys start up automaticly when i start my computer? 
how can i choose where to save my logs ?if i understood it right i will be able to
have the files sent to an external source, as email? for checking whats going on at
your home computer while not there...
and how do i make sure that the program runs in the background?

would really appreciate some help :)

---

