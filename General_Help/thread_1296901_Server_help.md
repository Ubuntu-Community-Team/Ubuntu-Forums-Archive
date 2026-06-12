---
title: "Server help"
date: 2009-10-21
forum: General Help
---

### Post by mooka91 on 2009-10-21
Alright, As i come across more problems on this steaming pile of crap i will post them.

Ive been asked to fix and maintain a Linux dedicated server for my friends.

It is in horrible shape. I'm not to good with Linux either xD.


I am attempting to clean out all the old useless apps on there, It has Webmin installed ([http://www.webmin.com](http://www.webmin.com)) but im not sure if the computer is utilizing anything from it. I tried accessing localhost:1000 but it fails. It is currently using a MySQL DB amongst an apache server running php openssl etc etc. But im not sure if it is using Webmins.

How will i find out if the server is using anything from this folder and if i can remove it.

It also appears he has MANUALLY installed everything (Probably cause his app manager wasn't working, Had to fix that =_=). The server appears to be running a home edition of Ubuntu (Yes i want to cry to) and no i cannot wipe the box. 

I am also trying to get ProFTPD onto the server... Well i managed to get it on there.... It also has about 16 copies of it on the bloody server, What is the best way to go about this, Uninstall my copy, Then manually delete the rest? Will this cause any errors? I don't want it trying to start something i deleted.

Thats all for now, But expect a few more xD.

Thank you in advance,

Mooka91.

---

### Post by egalvan on 2009-10-21
Unless it is a seven-nines-critical server,
then the "Home" edition of Ubuntu is probably adequate.
Especially if the hardware is not server-class, you will not notice much difference, if any.

The foundations are the basically the same.
Yes, the server kernel has some server-type optimizations, 
but again, you would need server-class hardware, and server-class loads,
to see much difference.

---

### Post by mooka91 on 2009-10-21
> **egalvan said:**
> Unless it is a seven-nines-critical server,
then the "Home" edition of Ubuntu is probably adequate.
Especially if the hardware is not server-class, you will not notice much difference, if any.

The foundations are the basically the same.
Yes, the server kernel has some server-type optimizations, 
but again, you would need server-class hardware, and server-class loads,
to see much difference.


[http://www.linxhosting.co.uk/dedicated-servers/](http://www.linxhosting.co.uk/dedicated-servers/)

The second plan.

---

