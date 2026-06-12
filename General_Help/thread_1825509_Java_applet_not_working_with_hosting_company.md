---
title: "Java applet not working with hosting company"
date: 2011-08-15
forum: General Help
---

### Post by volito on 2011-08-15
Java applet not working with hosting company? cannot connect and giving me error with [SIZE=-1]Sun Java Virtual Machine...

any simple fixes for this kinda annoying that i cannot connect to my hosting account :)

thanks
[/SIZE]

---

### Post by TBABill on 2011-08-15
Do you actually have Sun Java installed or open JDK? If you installed Ubuntu Restricted Extras, you do not have Sun Java installed yet. You need to go into software sources and enable the Canonical Partner Repository and then refresh your packages...or do a ```
sudo apt-get update
``` After that you can just search for the Sun Java Plugin and install it via Synaptic or Ubuntu Software Center. That should get you working better if you didn't have Sun Java installed before.

---

### Post by volito on 2011-08-15
ran update code and only see "JXplorer"

no plug ins if i search java tons of tools not sure which one will work for me

---

### Post by volito on 2011-08-15
```
Linux 2.6.38-10-generic-pae i386
Sun Microsystems Inc. -- Java(tm) 1.6.0_22

java.net.ConnectException: Connection refused
java.net.ConnectException: Connection refused
```this is error hosting is kicking back


tried with chrome also.....this is annoying..

---

### Post by volito on 2011-08-16
also installed [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]ubuntu-restricted-extras and still no go...


anyone use hostmonster and get there unlimited ftp to work with ubuntu?


[/FONT][/FONT][/COLOR]

---

### Post by volito on 2011-08-18
> **volito said:**
> also installed [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]ubuntu-restricted-extras and still no go...


anyone use hostmonster and get there unlimited ftp to work with ubuntu?


[/FONT][/FONT][/COLOR]


bump 

"what have to get mac or pc to do this"
has to be a better way


ok got sun java plugin install after following these instructions
[https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

still cannot get browsers to connect to hosting company

---

### Post by volito on 2011-09-02
> **volito said:**
> bump 

"what have to get mac or pc to do this"
has to be a better way


ok got sun java plugin install after following these instructions
[https://help.ubuntu.com/community/java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

still cannot get browsers to connect to hosting company


bump

---

