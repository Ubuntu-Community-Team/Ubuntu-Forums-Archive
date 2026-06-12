---
title: "starting clonezilla server with shortcut"
date: 2011-09-08
forum: General Help
---

### Post by Geosystems on 2011-09-08
Hello,
 
I'm running ubuntu 11.04 with clonezilla to send images to multiple clients.
The amount of pc's and image keep changing so i can't make the shortcut explained
in [http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/](http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/)
 
I would like to have a shortcut on the desktop to run the command that i now got to type in console: "sudo /opt/drbl/sbin/dcs" 
 
I don't mind typing the root password when I start the program (would be nice if i didnt have to) and that pc isnt connected to the internet
 
I've tried to make a file "start.sh" that contained only that command but that didnt work.
 
Thanks for helping me out!
 
George

---

### Post by Bodsda on 2011-09-08
> **Geosystems said:**
> Hello,
 
I'm running ubuntu 11.04 with clonezilla to send images to multiple clients.
The amount of pc's and image keep changing so i can't make the shortcut explained
in [http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/](http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/)
 
I would like to have a shortcut on the desktop to run the command that i now got to type in console: "sudo /opt/drbl/sbin/dcs" 
 
I don't mind typing the root password when I start the program (would be nice if i didnt have to) and that pc isnt connected to the internet
 
I've tried to make a file "start.sh" that contained only that command but that didnt work.
 
Thanks for helping me out!
 
George
 
Change the script to this
```

#! /bin/bash
sudo /opt/drbl/sbin/dcs

```
 
Then run
```

chmod a+x ~/Desktop/start.sh

```
 
Is this an ubuntu server or workstation install? (Graphics or CLI?)
 
Hope this helps,
Bodsda

---

### Post by btindie on 2011-09-08
Why not just put the script in your own bin directory?

If you don't have a ~/bin then create the directory, put your "start.sh" script in there. You don't need the ".sh" extension, it's not windows. Also it's best to change the name as there's already a binary called 'start', dcs-start. The important thing is to make sure it has the eXecutable permission set.
```
$ chmod +x ~/bin/dcs-start
```You can then just type "dcs-start" from a terminal.

If you edit /etc/sudoers WITH "sudo visudo", you can then set it so you don't need to enter a password to run the command.
> Cmnd_Alias   DCS = /home/geosystems/bin/dcs-start
geosystems      ALL=(ALL) NOPASSWD: DCS

---

### Post by Geosystems on 2011-09-08
Thanks for the fast reaction,
 
I allready had the script with 
```

#! /bin/bashsudo /opt/drbl/sbin/dcs 

```
 
But the CHMOD part made it work, thanks.
What exactly does this do?
 
I've got the workstation ubuntu installed because the other people at my work
will never get used to commandline only..
(i just keep trieing till something works or breaks..)

---

### Post by Bodsda on 2011-09-08
> **Geosystems said:**
> Thanks for the fast reaction,
 
I allready had the script with 
```

#! /bin/bashsudo /opt/drbl/sbin/dcs 

```
 
But the CHMOD part made it work, thanks.
What exactly does this do?
 
I've got the workstation ubuntu installed because the other people at my work
will never get used to commandline only..
(i just keep trieing till something works or breaks..)
 
It adds the execute permission to all users on that file.
 
Bodsda

---

