---
title: "Need help, Ubuntu apps randomly become unresponsive."
date: 2011-01-26
forum: General Help
---

### Post by jsel21 on 2011-01-26
OK so its been happening for a while. It seems like it usually occurs when I am on firefox. All of a sudden firefox will freeze and become unresponsive. When I try relaunching firefox, it will not open. Then I will try opening any other app like the calculator and get this messgage:

"Failed to execute child process
 'gcalctool' (input/output error)"

I get the same sort of messages with most other apps I try to open. Some applications will open with just a window box and nothing inside of it. I cannot view pictures I have saved either. When I try to restart the computer from the drop-down list on the top panel, ubuntu does absolutely nothing. If I try to ctrl-alt-delete, this error message pops up:

"Couldn't execute command: gnome-
 session-save --shutdown-dialog
 verify that this is a valid command."

The only way to shut down is by manual restart. Once I turn the computer back on, everything is back to normal, for atmost 15 minutes. Then this happens again. Thank you so much for any help.

---

### Post by acplusplusprogrammer on 2011-01-26
First try in the terminal:

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean

and then 

sudo touch /forcefsck

REBOOT

and see if it works. 


Otherwise read here:


Look here: [http://ubuntuforums.org/showthread.php?t=668840](http://ubuntuforums.org/showthread.php?t=668840)


Hope can help

---

### Post by jsel21 on 2011-01-29
> **acplusplusprogrammer said:**
> First try in the terminal:

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean

and then 

sudo touch /forcefsck

REBOOT

and see if it works. 


Otherwise read here:


Look here: [http://ubuntuforums.org/showthread.php?t=668840](http://ubuntuforums.org/showthread.php?t=668840)


Hope can help

Ok, I did everything you said and reinstalled firefox, but it still keeps doing this.

---

### Post by jsel21 on 2011-01-29
Update: Now I'm completely screwed. Grub will not load whatsover, so now i cannot boot into ubuntu or windows. When I turn my computer on, sometimes it will say "Operating system not found" or "Grub error: Cannot regonize partition", or something similar. This isn't the first time Ubuntu has completely failed me. My last installation of Ubuntu one day decided to not boot also.

---

