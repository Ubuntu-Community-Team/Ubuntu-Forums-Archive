---
title: "can not print to canon i250 connected to windows machine"
date: 2006-05-20
forum: General Help
---

### Post by electroconvulsive on 2006-05-20
I ahve a canon i250 connected to a winxp machine. This printer prints perfectly from the win machine but when i try to print a test page or anything else for that matter from my ubuntu machine the printers applet says that the job is printing but when I check in the printer queue on the win machine after about 15 seconds the job pops up as and dissapears as downloaded document. The error message in the printer applet on my ubuntu machine says: Unable to connect to Samba host will retry in 60 seconds, ERROR:Connection failed with error NT_STATUS_ACCESS_DENIED.

Since then I have added a user called root with the same password on the windows machine and I added the windows machine to my /etc/hosts files though this has cured the error message it is still not printing. Im all out of ideas and by the looks of things so is everyone on this forum on this issue and mu other post concerning my inability to use an external modem on this machine.
 
Is there anything I have missed in my Samba Config or has it got more to do with my windows Machine?

Is there anybody out there?

---

### Post by electrocutioner on 2006-06-15
I couldn't say for sure as I have yet to get samba working on my network,but there is definately a problem running a canon i250 in linux.There are people who have managed to get it going,but it is a lot of work.Even though the printer is on the winxp machine,you are trying to print over the network on a linux box and it will need it's native drivers running.Try and get the printer running from the linux box first,then attempt to do a network connect.

---

### Post by frogotronic on 2006-06-21
[QUOTE=electrocutioner]I couldn't say for sure as I have yet to get samba working on my network,but there is definately a problem running a canon i250 in linux.There are people who have managed to get it going,but it is a lot of work.Even though the printer is on the winxp machine,you are trying to print over the network on a linux box and it will need it's native drivers running.Try and get the printer running from the linux box first,then attempt to do a network connect.[/QUOTE]

Solution:

[http://www.ubuntuforums.org/showpost.php?p=1035129&postcount=54](http://www.ubuntuforums.org/showpost.php?p=1035129&postcount=54)

DO NOT put "guest@" in front of the hostname/printer name for DD.  This is a chaneg from BB.

Happy Printing!

---

