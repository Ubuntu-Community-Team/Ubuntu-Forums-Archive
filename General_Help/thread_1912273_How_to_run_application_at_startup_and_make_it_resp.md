---
title: "How to run application at startup and make it respawn"
date: 2012-01-20
forum: General Help
---

### Post by trafo23 on 2012-01-20
Hi,
how would it possible to automatically start an application when Ubuntu 11.10 starts up. It should also respawn, since synergyc crashes all the time in linux.

It seems that user upstart scripts are not allowed, what are the other options?

Thanks

---

### Post by BC59 on 2012-01-20
There are 2 ways to do it.
First open the Startup Applications from pushing the upper right wheel of the desktop. Keep it open.
Then push the dash from the opposite side and choose the application you like to put to start up. Then click and drag to the open Startup Applications window.

The other way is to go to /etc/xdg/autostart/ and copy a file of with extension .desctop. Paste it on the desktop and open a gedit. Find the file and open it. Should be like this:

> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Zeitgeist Datahub
Name[es]=Zeitgeist Datahub
Comment=Start the Zeitgeist Datahub for passive loggers
Comment[es]=Iniciar Zeitgeist Datahub para los monitores pasivos
Exec=zeitgeist-datahub
Terminal=false
Type=Application
Categories=
GenericName=
NoDisplay=true
X-GNOME-Autostart-Delay=20

Change the comments according to the application you like to put in autostart. Then save it with the name you like and the extension .desktop.
Run root nautilus
```
gksu nautilus
``` and with root nautilus paste the file again to /etc/xdg/autostart/
That's it

---

### Post by gsgleason on 2012-01-20
for a command line, this works:

while true
do
whatever command
done

---

### Post by SeijiSensei on 2012-01-20
The most straightforward way to start additional applications at boot is to put the start-up command in /etc/rc.local.  

I wrote a script that runs every few minutes out of cron and checks to see if all the servers I start are up and running by using the command "ps aux | grep program_name | grep -v grep". If that test turns up empty, the script restarts program_name.

---

### Post by dcstar on 2012-01-20
> **SeijiSensei said:**
> The most straightforward way to start additional applications at boot is to put the start-up command in /etc/rc.local.  
.........

Unfortunately that statement assumes that the person reading it knows the difference between GUI apps and non-GUI ones.

To many users do not know that they cannot run GUI apps from CRON or /etc/rc.local without the appropriate DISPLAY=:0 environment variable set to use the X server and then they post in these forums with "I can launch this in a terminal but not using xxxxx".

Be careful with blanket statements like that one above.

---

### Post by trafo23 on 2012-01-23
1) Regarding the rc.local proposal? This would not help with the respawning, is that correct?

2) I would like to restart the program instantly once it crashes. Upstart can do that, why do i need to write a shell script loop for that? What is the point of upstart in ubuntu 11.10 if it cannot be used?

3) What does the linux system itself use? It uses different things like xdg, rc.local, upstart etc etc? What is the "proper" way of doing it in ubuntu? Why are there SO MANY ways to do one thing?

Thanks

---

### Post by trafo23 on 2012-02-01
bump

---

### Post by Lars Noodén on 2012-02-01
#2) Upstart can be used, but it is new.  So how to use it has not become general knowledge and there is a relative shortage of material describing how to set it up compared to documentation on the old ways.  Upstart does have the ability to [respawn](http://upstart.ubuntu.com/wiki/Stanzas#respawn) processes.

---

