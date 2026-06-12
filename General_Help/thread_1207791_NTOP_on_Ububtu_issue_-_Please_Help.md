---
title: "NTOP on Ububtu issue - Please Help"
date: 2009-07-08
forum: General Help
---

### Post by Fidel M on 2009-07-08
I have recently installed Ubuntu in order to facilitate networking monitoring application called NTop, which I am sure that many of you are familar with.
 
Our company currently has 2 physical locations that are connected using a vpn tunnel. They both have individual subnets: 192.168.100.xxx and 192.168.101.xxx.
 
However when we run the Ntop application only the hosts of ONE location is recognized (the 192.168.101.xxx). 
 
Is there any way we can configure Ntop so as to have the hosts of BOTH locations be recognized? Any assistance will be greatly appreciated. Thanks!

---

### Post by Fidel M on 2009-07-08
Any help on this Guys?

---

### Post by synapsys on 2009-07-08
Have you looked in the configuration file?

/etc/ntop.conf

or the man page

man ntop

---

### Post by Fidel M on 2009-07-08
Thanks for the reply!

I went to that location but didn't see those files. What I'm seeing is:


[LIST]
[*]AS-List.txt
[*]etter.finger.os
[*]ntop-cert.pem
[*]oui.txt
[*]p2c.opt.table
[*]protocol.list
[*]specialMAC.txt
[/LIST]
Any other thoughts?

---

### Post by synapsys on 2009-07-08
If you look at the man page I'm sure there is a switch you can use to manually specify the local subnet(s) Then you can easily write a bash script for the command, or use it every time.

---

### Post by Fidel M on 2009-07-08
Sorry but I'm pretty new to this.

'Man' page? Any idea where I can find this file?

---

### Post by ajgreeny on 2009-07-08
man command in terminal is the man page, so in your case, open a terminal and type ```
man ntop
```magically, a page which is the manual for the command will appear, which you can scroll up and down easily to get information on the application or command.

For more info on man, and as an example do ```
man man
``` in terminal, and you will see what I mean.  this is usually available for every application and/or command in linux.

---

