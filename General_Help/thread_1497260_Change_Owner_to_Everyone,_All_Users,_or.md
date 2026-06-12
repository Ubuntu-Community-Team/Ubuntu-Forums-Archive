---
title: "Change Owner to Everyone, All Users, or *"
date: 2010-05-30
forum: General Help
---

### Post by XP1 on 2010-05-30
**Change Owner to Everyone, All Users, or ***

How do I change the owner of a folder to Everyone?

In Windows, I can just right click folder > Properties > Security > Edit... > Add... > Advanced... > Find Now > Select "Everyone" > OK > OK > Set Everyone permissions > OK > OK.
*^ See, so easy!*

Every time I login or restart, I have to launch these commands:
```
sudo chmod 777 /var/spool/cups/
sudo chmod 777 /var/spool/cups/*
```
I need to access the **/var/spool/cups/** spool folder, but having to re-do that is so annoying.

---

### Post by Lucky. on 2010-05-30
Looks like you've nailed it with the command prompt, though here's a very slightly shorter way:

> 
sudo chmod -R 777 /var/spool/cups


I don't know much about changing permissions using the GUI.  I really wish I did...seems like most linux users either get frustrated with the lack of power in the GUI and leave, or they pick up on the command prompt and stop using the GUI for anything useful.

Would be interesting to see a full admin guide using just the GUI...

In any case, somebody's probably going to ask you "Why does everyone need access to CUPS?"  Maybe there's another way to solve this problem than having you change permissions every time.  I'd ask, but I don't know enough about CUPS to help out.

---

### Post by sites on 2010-05-30
Why does everyone need access to CUPS?

(just trying to move things along, and curious where it will go)

---

### Post by Penguin Guy on 2010-05-30
Add any commands you want to run at startup to your [FONT="Courier New"].bashrc[/FONT].
```
sudo chmod -R 777 /var/spool/cups
```

I know this is getting a bit repetitive, but; why does everyone need access to CUPS?

---

### Post by XP1 on 2010-05-30
> **sites said:**
> Why does everyone need access to CUPS?LOL, I'm using Ubuntu in a virtual machine and I need to copy the spool files into a folder on my Windows machine. I have other test accounts in Ubuntu that will need access to that folder as well.

Problem is: The permissions keep resetting when I do that chmod after I restart or print a new file. Maybe changing the owner to Everyone will fix it?

> **Penguin Guy said:**
> Add any commands you want to run at startup to your [FONT="Courier New"].bashrc[/FONT].
```
sudo chmod -R 777 /var/spool/cups
```
Also, I just remembered: Setting the command at startup won't work well because new files that are dumped into the spool folder are automatically set back to the original root permissions. :(

---

### Post by ssam on 2010-05-30
would it be easier to just print to file? in linux you can always print to a pdf or ps file.

or get windows to share the printer to the network, and connected to it over the network from the virtual ubuntu.

---

### Post by XP1 on 2010-05-30
> **ssam said:**
> would it be easier to just print to file? in linux you can always print to a pdf or ps file.

or get windows to share the printer to the network, and connected to it over the network from the virtual ubuntu.I am already saving the PDF using cups-pdf, but I also want to save the spool file for archival purposes because it contains the printer and other information.

*(I only save the spool file for special documents. Most times, I don't save it.)*

---

### Post by dino99 on 2010-05-30
mountmanager deals with partitions and devices rights

---

### Post by ssam on 2010-05-30
maybe this trick will work
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by XP1 on 2010-06-04
> **ssam said:**
> maybe this trick will work
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)Thanks, it works. Now, spool files from the future will no longer have root-only permissions.

I just had to add this command to run at startup (I added it to /etc/init.d/rc.local):
```
sudo bindfs -o perms=0777,mirror=administrator,group=users /var/spool/cups /var/spool/cups
```
Not as easy as Windows, though.

---

### Post by Penguin Guy on 2010-06-05
> **XP1 said:**
> Not as easy as Windows, though.
More secure than Windows, though.

---

