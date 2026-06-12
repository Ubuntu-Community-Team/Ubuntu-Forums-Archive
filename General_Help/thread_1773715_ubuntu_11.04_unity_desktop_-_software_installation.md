---
title: "ubuntu 11.04 unity desktop - software installation problems -; ' input/output error'"
date: 2011-06-02
forum: General Help
---

### Post by creuynni on 2011-06-02
Hi- i'm fairly new to ubuntu, and seem to have had problem after problem- though i'm perservering...as someone who works with gift economy, i guess it makes sense for me to use ubuntu...

This time, I can't find a solution on the forums etc for this problem,
The other day I updated to 11.04. And it's using the Unity desktop.


I didn't clear the packages when i updated, I clicked 'Keep them' rather than 'clear them', as when i tried updating to 11.04 before it didn't work, so i thought i'd try not clearing those packages, and see if it would install correctly then. And it did work, it has installed, and many of the installed programs e.g. firefox, librewrite seem to be working fine.... but.....

 it's not letting me install any other software. Whichever software i'm tried from the ubuntu software manager, or the  package installation manager (sudo apt etc) which i tried after reading stuff on forums. It goes to about 95 % then fails.
 I've tried installing things like 'ubuntu restricted', 'flash', 'education ubuntu' plus a few other education softwares.
 Both ways of installing these have similar messages,
  I also tried the Compiz config installation via 'Terminal',  as desribed on a tips and tricks for 1..04 thread which also didn't work.
 
 i couldn't copy and paste the error from  the synaptic package manager, it ended searching for something that it didn't find, with the same error message as the bottom line of the software centre installation. Here is a copy and paste of the msgs I did receive ; 
“
 InstallArchives() failed:  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
 Selecting previously deselected package adobe-flashplugin. 
 (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error 
 

 

  
 Preconfiguring packages ... 
 Preconfiguring packages ... 
 (Reading database ...  
 (Reading database ... 5%% 
 (Reading database ... 10%% 
 (Reading database ... 15%% 
 (Reading database ... 20%% 
 (Reading database ... 25%% 
 (Reading database ... 30%% 
 (Reading database ... 35%% 
 (Reading database ... 40%% 
 (Reading database ... 45%% 
 (Reading database ... 50%% 
 (Reading database ... 55%% 
 (Reading database ... 60%% 
 (Reading database ... 65%% 
 (Reading database ... 70%% 
 (Reading database ... 75%% 
 (Reading database ... 80%% 
 (Reading database ... 85%% 
 (Reading database ... 90%% 
 (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error 
 

 ….............
 installArchives() failed:  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
 Selecting previously deselected package freepats. 
 (Reading database ...  
 (Reading database ... 5%% 
 (Reading database ... 10%% 
 (Reading database ... 15%% 
 (Reading database ... 20%% 
 (Reading database ... 25%% 
 (Reading database ... 30%% 
 (Reading database ... 35%% 
 (Reading database ... 40%% 
 (Reading database ... 45%% 
 (Reading database ... 50%% 
 (Reading database ... 55%% 
 (Reading database ... 60%% 
 (Reading database ... 65%% 
 (Reading database ... 70%% 
 (Reading database ... 75%% 
 (Reading database ... 80%% 
 (Reading database ... 85%% 
 (Reading database ... 90%% 
 (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error   “
 

 
I also did try using computer janitor to clear up files, but it just had errors, and was unable to do so.
I also did a 'check update', and clicked to update a software which was there, but it came up with the same error message input/output error etc.


Thanks for reading. Any help is much appreciated. I would like to keep on using Ubuntu if I can.

---

### Post by iclestu on 2011-06-02
> **creuynni said:**
> Hi- i'm fairly new to ubuntu, and seem to have had problem after problem- though i'm perservering...as someone who works with gift economy, i guess it makes sense for me to use ubuntu...

This time, I can't find a solution on the forums etc for this problem,
The other day I updated to 11.04. And it's using the Unity desktop.


I didn't clear the packages when i updated, I clicked 'Keep them' rather than 'clear them', as when i tried updating to 11.04 before it didn't work, so i thought i'd try not clearing those packages, and see if it would install correctly then. And it did work, it has installed, and many of the installed programs e.g. firefox, librewrite seem to be working fine.... but.....

 it's not letting me install any other software. Whichever software i'm tried from the ubuntu software manager, or the  package installation manager (sudo apt etc) which i tried after reading stuff on forums. It goes to about 95 % then fails.
 I've tried installing things like 'ubuntu restricted', 'flash', 'education ubuntu' plus a few other education softwares.
 Both ways of installing these have similar messages,
  I also tried the Compiz config installation via 'Terminal',  as desribed on a tips and tricks for 1..04 thread which also didn't work.
 
 i couldn't copy and paste the error from  the synaptic package manager, it ended searching for something that it didn't find, with the same error message as the bottom line of the software centre installation. Here is a copy and paste of the msgs I did receive ; 
“
 InstallArchives() failed:  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
 Preconfiguring packages ... 
 Selecting previously deselected package adobe-flashplugin. 
 (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error 
 

 

  
 Preconfiguring packages ... 
 Preconfiguring packages ... 
 (Reading database ...  
 (Reading database ... 5%% 
 (Reading database ... 10%% 
 (Reading database ... 15%% 
 (Reading database ... 20%% 
 (Reading database ... 25%% 
 (Reading database ... 30%% 
 (Reading database ... 35%% 
 (Reading database ... 40%% 
 (Reading database ... 45%% 
 (Reading database ... 50%% 
 (Reading database ... 55%% 
 (Reading database ... 60%% 
 (Reading database ... 65%% 
 (Reading database ... 70%% 
 (Reading database ... 75%% 
 (Reading database ... 80%% 
 (Reading database ... 85%% 
 (Reading database ... 90%% 
 (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error 
 

 ….............
 installArchives() failed:  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
  
 Extract templates from packages: 63%% 
 Extract templates from packages: 100%% 
 Selecting previously deselected package freepats. 
 (Reading database ...  
 (Reading database ... 5%% 
 (Reading database ... 10%% 
 (Reading database ... 15%% 
 (Reading database ... 20%% 
 (Reading database ... 25%% 
 (Reading database ... 30%% 
 (Reading database ... 35%% 
 (Reading database ... 40%% 
 (Reading database ... 45%% 
 (Reading database ... 50%% 
 (Reading database ... 55%% 
 (Reading database ... 60%% 
 (Reading database ... 65%% 
 (Reading database ... 70%% 
 (Reading database ... 75%% 
 (Reading database ... 80%% 
 (Reading database ... 85%% 
 (Reading database ... 90%% 
 (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting: 
  reading files list for package 'libgail-gnome-module': Input/output error   “
 

 
I also did try using computer janitor to clear up files, but it just had errors, and was unable to do so.
I also did a 'check update', and clicked to update a software which was there, but it came up with the same error message input/output error etc.


Thanks for reading. Any help is much appreciated. I would like to keep on using Ubuntu if I can.

try these
```

sudo dpkg --configure -a
```

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by creuynni on 2011-06-03
thanks loads, but none of those worked.
i had messages like 'read only'files, and file not found error, and locked file. i did write it in libre office the erro messages, but it suddenly closed down after one of those tries

and now, after doing that, my libre office (all libre software) isn't working, 

synaptic package manage is now not working too, it just comes up with a small empty box like an error message, but with no error message

and now terminal is not working, just comes wth a blank terminal screen, with no writing happening on it.

i will try a reboot to see if any of the recent problems changes, but those suggestions, unfortuntely didnt work.
perhaps i ought to just go back to ubuntu 10.10?

---

### Post by creuynni on 2011-06-03
the libre office etc are working again, but still having the same problem with trying to install software.
i've tried repairing packages option on the startup too, with no success.

i think i'm going to have to go back to ubuntu 10.10 or something, unless anyone else has any suggestions?

---

