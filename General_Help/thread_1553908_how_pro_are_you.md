---
title: "how pro are you?"
date: 2010-08-15
forum: General Help
---

### Post by UnstableAfliction on 2010-08-15
how pro are you? solve this little problem...

i want to put the close, minimize, unminimize, buttons left of the window but my window manager doesnot start,  (my window manager is xfmwf4), i guess this is happening because compiz fusion. i install meta-city, and i use meta-city --replace, but it works only until restart the PC, and don't have a menu or something like that to set the buttons order.

other thing... is there a command for check the OS looking for buggs, errors or broken packages? i do install some programs, some of the doesn't work like have to be.


please help, and excuse me for the awful English.

---

### Post by bobcollard on 2010-08-16
> **UnstableAfliction said:**
> how pro are you? solve this little problem...

i want to put the close, minimize, unminimize, buttons left of the window but my window manager doesnot start,  (my window manager is xfmwf4), i guess this is happening because compiz fusion. i install meta-city, and i use meta-city --replace, but it works only until restart the PC, and don't have a menu or something like that to set the buttons order.

other thing... is there a command for check the OS looking for buggs, errors or broken packages? i do install some programs, some of the doesn't work like have to be.


please help, and excuse me for the awful English.
Actually you should find it under the Settings>Xfce4 Settings Manager>Window Manager.  Then choose a Theme that has the Buttons available for moving, (some don't).  See attached.
Other thing?  Open Synaptic Pacakge Manager and look at the bottom of the menu.  If there are any broken packages you may see them there and use the same manager to repair them.

---

### Post by bobcollard on 2010-08-16
duplicate delete

---

### Post by UnstableAfliction on 2010-08-16
thats in fact the problem... when i go xfc setting manager, and click on window manager, nothing happen.

tanks for the reply.

---

### Post by bodhi.zazen on 2010-08-16
Most likely it is some kind of corruption in your xfce configuration.

Delete the xfce configuration files in your home or try a new test user.

XFCE seems to like to do this sometimes, often times when testing / customizing new themes.

---

### Post by linux18 on 2010-08-16
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade

---

### Post by UnstableAfliction on 2010-08-16
i proved all what you say, but the problem still, when i open window manager nothing happen. this is maybe about compiz dont you think? 

tanks for the reply.

---

### Post by bodhi.zazen on 2010-08-17
> **UnstableAfliction said:**
> i proved all what you say, but the problem still, when i open window manager nothing happen. this is maybe about compiz dont you think? 

tanks for the reply.

I can not tell from your post. Simply stating there is a problem and asking for a guess as to the nature of the problem is not likely to solve the problem.

So what if it is compiz, then what ?

You need to tell us what you have done to try to fix the problem.

Did you make a new user or remove your xfce settings from the old user ? If so, what happened ?

---

### Post by UnstableAfliction on 2010-08-24
thx for the reply, (you can be polite the next), i do create a new user, there i can configure the windows how i want, but when i start compiz all the work spoils.

this is the command out:

some@thing-desktop:~$ compiz
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator

(gtk-window-decorator:4815): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
Advertencia del gestor de ventanas: Ocurrió un error al cargar el tema  «Clearlooks»: Falló al encontrar un archivo válido para el  temaClearlooks


please help, i know i am lol but don't nag me for this.

---

### Post by bodhi.zazen on 2010-08-24
I am sorry, but I am not sure about that one.

I would suggest you post a bug report against compiz on launchpad, post the error message as you did here.

---

### Post by UnstableAfliction on 2010-08-24
this is all?

---

### Post by linux18 on 2010-08-25
install emerald

---

### Post by UnstableAfliction on 2010-08-26
JA, i cant belive that the solution was so easy, ja, thx man, after install beryl i edit the order whit  a simple code. thx man. i guess this is solved

---

### Post by linux18 on 2010-08-26
glad it works!
time to mark the thread as solved...

---

