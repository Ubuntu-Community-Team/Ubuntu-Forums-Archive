---
title: "Command for closing a running program"
date: 2010-01-03
forum: General Help
---

### Post by Timster4life on 2010-01-03
First off, Thank you for the hep that I will hopefully receive, I have referenced this forum many times, but first time posting! ^_^

Beforehand let me warn you, Completely NEW at this...I know less than the basics
I've been a sole windows box guy for sometime, just install xubuntu 9 on an old laptop to learn/try and I really enjoy it, but...of course having some problems. 


I am trying to run a vent server off of the machine since it primarily sits on my desk at home..now the server has been installed and everything is running (kind of) correctly, I can log in and all that jazz..however..how in the heck do you close the program??

Say I make a change to the .INI file and want to restart the server...what do i type in terminal

All i'm doing to get it to run is  ./Ventrilo_srv , I don't know the command to get it to shutdown properly so I can adjust the .INI and restart the server...please help!!

---

### Post by Bobulous on 2010-01-03
[COLOR=Black]Well, this page seems relevant:

[http://www.andreas-glaser.com/2008/06/15/ventrilo-linux-server-startscript/](http://www.andreas-glaser.com/2008/06/15/ventrilo-linux-server-startscript/)

Looks like the Ventrilo command doesn't offer a handy restart option, so the script in that blog simply reads the ventrilo_srv.pid[COLOR=#ff0000] [/COLOR][/COLOR][COLOR=Black]file to get the process ID number, and then just uses the kill command to end the process with that ID number. Which kills the Ventrilo process.

Ventrilo really doesn't seem to offer much in the way of support for their Linux client, so there may be a better way than this, but I can't see it.[/COLOR] [COLOR=Black][COLOR=#ff0000]
[/COLOR][/COLOR]

---

### Post by Bobulous on 2010-01-03
(Ignore this. An edit fixed the problem to which this post referred.)

---

### Post by Timster4life on 2010-01-03
> **Bobulous said:**
> [COLOR=Black]Well, this page seems relevant:

[http://www.andreas-glaser.com/2008/06/15/ventrilo-linux-server-startscript/](http://www.andreas-glaser.com/2008/06/15/ventrilo-linux-server-startscript/)

Looks like the Ventrilo command doesn't offer a handy restart option, so the script in that blog simply reads the ventrilo_srv.pid[/COLOR][COLOR=Black]file to get the process ID number, and then just uses the kill command to end the process with that ID number. Which kills the Ventrilo process.

Ventrilo really doesn't seem to offer much in the way of support for their Linux client, so there may be a better way than this, but I can't see it.[/COLOR] [COLOR=Black][COLOR=#ff0000]
[/COLOR][/COLOR]
  

 Thank you so much, I will make sure to try it out ASAP..as sad as it sounds I've been restarting the machine every time I make a small change to the .INI..I knew there had to be SOME better way! 

Much appreciated for the help again!

---

### Post by k64 on 2010-01-03
> **Timster4life said:**
> First off, Thank you for the hep that I will hopefully receive, I have referenced this forum many times, but first time posting! ^_^

Beforehand let me warn you, Completely NEW at this...I know less than the basics
I've been a sole windows box guy for sometime, just install xubuntu 9 on an old laptop to learn/try and I really enjoy it, but...of course having some problems. 


I am trying to run a vent server off of the machine since it primarily sits on my desk at home..now the server has been installed and everything is running (kind of) correctly, I can log in and all that jazz..however..how in the heck do you close the program??

Say I make a change to the .INI file and want to restart the server...what do i type in terminal

All i'm doing to get it to run is  ./Ventrilo_srv , I don't know the command to get it to shutdown properly so I can adjust the .INI and restart the server...please help!!


You would type "sudo killall" followed by the name of the program. The "sudo" command gives you root access, and "killall" kills all processes involved in a program.

---

### Post by blueridgedog on 2010-01-03
> **k64 said:**
> You would type "sudo killall" followed by the name of the program. The "sudo" command gives you root access, and "killall" kills all processes involved in a program.

Note that you will not need "sudo" unless it is a system or someone elses process. If you want to kill firefox for example, 

```
killall firefox 
```

is sufficient.

Type 

```
man killall
``` 

for more information.

---

