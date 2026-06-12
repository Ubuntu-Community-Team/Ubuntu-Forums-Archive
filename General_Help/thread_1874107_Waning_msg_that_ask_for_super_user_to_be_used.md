---
title: "Waning msg that ask for super user to be used"
date: 2011-11-02
forum: General Help
---

### Post by bjch512 on 2011-11-02
Hi,
 
I'm new in Ubuntu and got a question on super user account of Ubuntu.  It would be appreciated if someone could help.
 
When we run commands, which need super user privilige, in normal user account, Ubuntu will show messages like:
 
[COLOR=red][FONT=Courier New]requested operation requires superuser privilege[/FONT][/COLOR]
[COLOR=red][FONT=Courier New][/FONT][/COLOR] 
[COLOR=red][FONT=Courier New][COLOR=red][FONT=Courier New]only root can do that[/FONT][/COLOR]
[COLOR=red][FONT=Courier New][/FONT][/COLOR] 
[COLOR=red][FONT=Courier New][COLOR=black]However, I converted a RH RPM with Alien, after installing the converted Debian package on Ubuntu 10.4, I didn't see such warning messages when running the converted utility.  It just failed silently.[/COLOR][/FONT][/COLOR]
[COLOR=red][FONT=Courier New][COLOR=black][/COLOR][/FONT][/COLOR] 
[COLOR=red][FONT=Courier New][COLOR=black]Could someone please tell me where the warning messages come from, and how to let Ubuntu to show this message when I run the converted utility?[/COLOR][/FONT][/COLOR]
[COLOR=red][FONT=Courier New][/FONT][/COLOR] 
[COLOR=red][FONT=Courier New][COLOR=black]Thanks,[/COLOR][/FONT][/COLOR]
[COLOR=red][FONT=Courier New][COLOR=black]BJ[/COLOR][/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2011-11-02
sudo is for terminal command
gksudo is for root gui programs (like the update manager)
sudo example
instead of[FONT=Courier New] apt-get update[/FONT] use [FONT=Courier New]sudo apt-get update[/FONT]
gksu example
instead of [FONT=Courier New]gparted[/FONT] use [FONT=Courier New]gksu gparted[/FONT]

as for the fail silently i assume this was in a attempt to open the got via launcher with out root access
try using a script to process the exit code/text

---

### Post by haqking on 2011-11-02
read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") for usage and terms

---

### Post by bjch512 on 2011-11-02
[FONT=Arial][SIZE=3]I know how to use sudo to run my converted utilited on Ubuntu.  My questions are:[/SIZE][/FONT]
[FONT=Arial][SIZE=3][/SIZE][/FONT] 
[FONT=Arial][SIZE=3](1) Where the warning messages come from?[/SIZE][/FONT]
[FONT=Arial][SIZE=3](2) How to let Ubuntu show the message when I run the converted utility, which needs super user priviledge, as normal user?

Thanks![/SIZE][/FONT]
[FONT=Arial][SIZE=3]BJ[/SIZE][/FONT]

---

