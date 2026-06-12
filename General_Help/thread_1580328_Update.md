---
title: "Update"
date: 2010-09-23
forum: General Help
---

### Post by GhOsT un1T on 2010-09-23
Can someone tell me how can i undo an update that i maded for ubuntu ..

Because that update is slowing my computer..

---

### Post by GhOsT un1T on 2010-09-23
is someone gonna help me ?

---

### Post by ptptaylor on 2010-09-23
Patience is a virtue...

I don't know how to roll back an update, but you can just uninstall it in the synaptic package manager and then install the version which you want to install.
What is it you updated exactly?

---

### Post by GhOsT un1T on 2010-09-23
> **ptptaylor said:**
> Patience is a virtue...

I don't know how to roll back an update, but you can just uninstall it in the synaptic package manager and then install the version which you want to install.
What is it you updated exactly?


i don t know bro but my pc is runing slowly

---

### Post by ptptaylor on 2010-09-23
Ok so open up the synaptic package manager, go to file-->history. Take a look at the date when the update was installed and see what has been updated/changed.

---

### Post by dino99 on 2010-09-23
what is that update ?

into synaptic (system admin synaptic), you can select this package for reinstallation, or into a console to reconfigure it:

sudo dpkg-reconfigure thatfilewhichmakeyoumad

sudo dpkg --configure -a
(will reconfigure all the system for ease)

sudo apt-get install -f
(check for missing files)

but you might watch logs (system admin logviewer) to find errors and into .xsession-errors (hiden file into /home, unhide it with ctrl+h), but what hardware is in use ?

if you really want to downgrade that file, not so easy by the way as dependencies might be different), you can find it there: 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
then download it and force installation

---

### Post by GhOsT un1T on 2010-09-23
no bro i just don t want to backup one file but the hole update is making me mad but i don t know how to remove it

---

### Post by GhOsT un1T on 2010-09-23
Can someone contact via team viewer and fix that ??

---

### Post by s0rc3r3r on 2010-09-23
I think rolling back updates is not a good idea as Ubuntu updates are crucial in some cases for the overall stability of your computer system

1)You can find which application is slowing down your computer and there are many ways to make those applications faster by tweaking it.

2)If you dont want updates to be automatic. you can go to the SYSTEM->ADMINISTRATION->UPDATE MANAGER.

Click on Settings
Click on 'UPDATE' Tab
and change the settings to 'Only Notify about available Updates'

This wont install the updates automatically, but notify you  of the same.
Then you can decide if you want to install it nor not.

I would say, tune the application that is slowing down and make it functional rather than roll back the update and compromise your system.

---

### Post by dino99 on 2010-09-23
> **GhOsT un1T said:**
> Can someone contact via team viewer and fix that ??

how much you pay ?

---

### Post by GhOsT un1T on 2010-09-23
> **dino99 said:**
> how much you pay ?

for free bro

---

