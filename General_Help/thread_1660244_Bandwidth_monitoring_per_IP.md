---
title: "Bandwidth monitoring per IP"
date: 2011-01-05
forum: General Help
---

### Post by CNM on 2011-01-05
Hello all ,

My problem is the following :
I have a certain Internet connection for a certain network.
So many people are sharing this network.
What i need is a software on Linux (preferably Ubuntu) that will enable me to monitor the bandwidth usage PER IP !!!
Like : ip x.x.x.x using 20Kb upload 200Kb download , connected to this site for example ...

The main goal is to know from which IP is the high Upload traffic or download traffic is coming , because i have a certain quota and I'm always getting over the quota (in upload and download) and end up paying extra for the ISP , so i would need to know who is using lots of upload/download bandwidth ...

Thanks :)

---

### Post by claydon on 2011-01-05
depending on your network config ntop allows you to do this, it includes live graphs showing usage and keeps the records for you to view after. It will also show how much bandwidth people have used. 

You can get it from the Ubuntu package manager and installation is pretty painless.

you will need to capture the data at the point your broadband is split (prob. via a mirrored port)

---

### Post by CNM on 2011-01-05
After installing it from the software center , what to do to launch it ?
i read i have to invoke this command : sudo ntop -P /usr/local/lib/ntop/
then go to : [http://localhost:3000/](http://localhost:3000/)
however the page does not load ... what to do

P.S
i already have Apache2 installed
(apt-get install apache2) and it's running ok

---

### Post by claydon on 2011-01-05
from a terminal 

sudo ntop -u <user>

it will then ask you to create a username and password for the admin user (ntop)

a whole load of lines will appear on the screen and you should then be able to browse to localhost:3000

---

### Post by CNM on 2011-03-07
> **claydon said:**
> from a terminal 

sudo ntop -u <user>

it will then ask you to create a username and password for the admin user (ntop)

a whole load of lines will appear on the screen and you should then be able to browse to localhost:3000

Sorry for the late reply i was sooo busy lately ...
actually i installed ntop on ubuntu 10.10
however i cannot figure out how to check the upload/download size that a certain IP address did ...

any help would be highly appreciated :)

thanks

---

### Post by CNM on 2011-03-08
here's my problem
i have a firewall with 3 subnets 
i want to monitor which IPs of the 3 subnets are consuming the most bandwidth (in MB ...)
since i have 2 interfaces for internal network connected between the firewall and my core switch , i connected them from the FW to a switch and mirrored the 2 switch ports to a monitor port on wich i connected ntop (installed on an ubuntu VM) and then connected two other switch ports from the switch (i am using for mirroring cause i don't have a hub) to the core switch ...
however , i am not able to see the consumption per IP ...

can anyone help me with that ?

---

### Post by CNM on 2011-03-11
> **CNM said:**
> here's my problem
i have a firewall with 3 subnets 
i want to monitor which IPs of the 3 subnets are consuming the most bandwidth (in MB ...)
since i have 2 interfaces for internal network connected between the firewall and my core switch , i connected them from the FW to a switch and mirrored the 2 switch ports to a monitor port on wich i connected ntop (installed on an ubuntu VM) and then connected two other switch ports from the switch (i am using for mirroring cause i don't have a hub) to the core switch ...
however , i am not able to see the consumption per IP ...

can anyone help me with that ?


solved that
you have to run ntop with the option "-c" just in case someone faces the problem :)
actually the "-c" option enables the sticky host feature 
by default ntop collects traffic info about running hosts
once a host goes idle ntop automatically purges infos collected ... and that's what was happening with me ... once a host goes idle , the infos gets purged and i cannot see how much bandwidth he's using for example ...
by using the "-c" option , you enable the sticky hosts feature so that even if a host goes idle the info collected are not purged
however they will be purged if ntop is stopped ...

---

