---
title: "wine installation"
date: 2010-07-17
forum: General Help
---

### Post by thewho1050 on 2010-07-17
I tried to install wine from Software sources and the terminal.  this is the response i got from terminal:

sudo apt-get install wine1.2
brandon@brandon-laptop:~$ sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.2: Depends: libaudio2 but it is not installable
           Recommends: winbind but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed
E: Broken packages

can anyone help me?

---

### Post by jschilli1 on 2010-07-17
Hi, All!

Try installing WINE through package manager. Just launch package manager, search WINE, and click on the WINE Microsoft Windows Compatibility Layer (beta release).

-JS1

---

### Post by thewho1050 on 2010-07-17
i had tried that before i used terminal.  
the error message i recieved there is as follows

[SIZE="4"]Package dependencies cannot be resolved[/SIZE]
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

anything else?

---

### Post by watupgroupie on 2010-07-17
Try removing the Wine PPA. Install the default version of Wine. Add the Wine PPA back in and do an update.

---

### Post by thewho1050 on 2010-07-17
I dont know how to do that.  Besides, i cant find wine on the system anywhere.

---

### Post by watupgroupie on 2010-07-18
What do you mean you can't find Wine on the system anywhere? Do you mean on your system, cause I don't think you've actually installed it yet. I read on the WineHQ forum that people had issues when they tried to install Wine using wine1.2 try just doing ```
sudo apt-get install wine
``` and see what it does. Also, have you changed your sources list at all to add the Wine PPA?

---

