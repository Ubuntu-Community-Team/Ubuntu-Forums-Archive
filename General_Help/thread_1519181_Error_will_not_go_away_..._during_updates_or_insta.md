---
title: "Error will not go away ... during updates or installing a program"
date: 2010-06-27
forum: General Help
---

### Post by Dodeca on 2010-06-27
Hello All

I installed and then uninstalled FlightGear ... a flight simulator.
and then Ubuntu Tweak told me a file from that package was still on my computer ( 10.04 64 )
I let Ubuntu Tweak "fix" it ...

Since then when I do any update or install I get this ...

Processing triggers for man-db ...
Setting up fgfs-base (1.9.0-1) ...
ln: creating symbolic link `/usr/share/games/FlightGear/Timezone': No such file or directory
dpkg: error processing fgfs-base (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 fgfs-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

Help ??? - I don't care if the file remains

---

### Post by Spr0k3t on 2010-06-27
Try this ([#]("https://help.ubuntu.com/community/SynapticHowto#Broken%20Upgrade%20or%20Installation"))

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Should fix the issue and force the removal of the symbolic link.

---

### Post by Dodeca on 2010-06-27
> **Spr0k3t said:**
> Try this ([#]("https://help.ubuntu.com/community/SynapticHowto#Broken%20Upgrade%20or%20Installation"))

```
sudo dpkg --configure -a
sudo apt-get install -f
```Should fix the issue and force the removal of the symbolic link.

Did NOT work :(
Did both .. in that order also with autoremove!


xxx@xxx-hp-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fgfs-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fgfs-base (1.9.0-1) ...
ln: creating symbolic link `/usr/share/games/FlightGear/Timezone': No such file or directory
dpkg: error processing fgfs-base (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 fgfs-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


also tried autoremove ... thanks 4 the try !

---

### Post by Spr0k3t on 2010-06-27
Here's a thought... check to see if the directory /usr/share/games/FlightGear/ exists.  If it doesn't, then create it.  From there, try the autoremove again.

---

### Post by Dodeca on 2010-06-27
> **Spr0k3t said:**
> Here's a thought... check to see if the directory /usr/share/games/FlightGear/ exists.  If it doesn't, then create it.  From there, try the autoremove again.


Nope ...

xxx@xxx-hp-laptop:~$ ls /usr/share/games/
FlightGear  gbrainy

xxx@xxx-hp-laptop:~$ sudo apt-get autoremove fgfs-base
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fgfs-base
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 468MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151725 files and directories currently installed.)
Removing fgfs-base ...
dpkg: error processing fgfs-base (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 fgfs-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


Nope NADA

---

### Post by Dodeca on 2010-06-27
> **Spr0k3t said:**
> Here's a thought... check to see if the directory /usr/share/games/FlightGear/ exists.  If it doesn't, then create it.  From there, try the autoremove again.

Actually ... It worked ...

I reinstalled flightgear from software center then removed it

ALL FIXED

THANKS to [B]Spr0k3


[/B]

---

### Post by Spr0k3t on 2010-06-28
Good to hear!  Make sure you mark the thread as solved using the thread tools link above.

---

