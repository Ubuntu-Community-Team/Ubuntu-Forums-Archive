---
title: "ubuntu 11.04 big problem"
date: 2011-05-15
forum: General Help
---

### Post by kadlam on 2011-05-15
[SIZE=2]Evidently, I messed with the wrong file manager. I was having problems with Nautilus and decided to 
 
sudo apt-get remove nautilus
 
Then I re-booted the machine and now have big-time troubles.
 
ON START-UP, I get the following flags:
 
- Could not update ICE authority file /home/mycomputer/.ICE authority X Close
 
- There is a problem with the configuration server
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
 
- Could not apply the stored configuration for monitors
 
When I try to open terminal I see the following:
 
bash: /home/kadlam/.bashrc: Permission denied
 
If I try to execute anything I am denied permission - including sudo.
 
help!
[/SIZE]

---

### Post by lakerssuperman on 2011-05-15
Have you tried using the Recovery Mode option in Grub?  This will drop you to a command line interface with root access.  From there you should be able to sudo apt-get install nautilus.

---

### Post by kadlam on 2011-05-16
[INDENT]thanks lakerssuperman...
[/INDENT] 
Yes, right after I sent the last message I did just that. I got apt-get to install nautilus but the problems remain the same. Now, at least I can operate from terminal under root but I don't know exactly what to try next. I looked at the sudoers file and it appears ok. I also did 'adduser username admin' and verified that my username is already a member of 'admin'
 
After all this I go back to normal boot only to have the same issues repeat. I imagine there is much I can try from the root terminal but it's a bit beyond me at this point. Still looking for advice.

---

### Post by shashanksingh on 2011-05-16
it seems it removed some other important thing along with nautilus.

try this

Ctr+Alt+f1

login to tty1

sudo apt-get install nautilus.


Next time remove it from synaptic and be careful as to what all you are removing

---

### Post by kadlam on 2011-05-16
Thank you but I continue to get the same notices when I re-boot
 
[SIZE=2][INDENT]Could not update ICE authority file /home/mycomputer/.ICE authority X Close
 
There is a problem with the configuration server(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
 
Could not apply the stored configuration for monitors....etc
[/INDENT]Once I have the desktop up, nothing appears under Applications, in Places I cannot get into the /home directory for lack of permission and in System i don't have any of the selections normal to admin. And if I try to operate from terminal mode, I have no permission to do anything. Very strange.
[/SIZE]

---

### Post by kadlam on 2011-09-17
NOTE TO SELF:

The problem was not ever figured out but was resolved by a re-install of 11.04.

---

