---
title: "How to install .run file??/"
date: 2010-12-08
forum: General Help
---

### Post by prashant699 on 2010-12-08
Hey first of all .... i am newbi.
I recently installed ubuntu in my system. to enable extra effects, i shud have nvidia drivers. problem is that corrently my comp. is in offline mode and so, i head over to a internet cafe and downloaded mah driver file (it is .run file)....
Then when i tried to install it, it (in terminal) said that i shud run it as root.... wtf!!!! i dont even know what is root!!!!'
sumbody help me!!!!

---

### Post by gandaran on 2010-12-08
use sudo to run/install the file, sudo gives you temporary root permissions,
```
sudo sh mane_of_file_to_install.run
``` 
or type [COLOR="DarkRed"]sudo -i[/COLOR] in terminal and enter to run root terminal

but you should try installing the driver from system » administration » hardware drivers, 
from the internet cafe wi-fi connection run the update software package list command
> sudo apt-get update
then look in system » administration » hardware drivers and enable the driver.

---

### Post by TeoBigusGeekus on 2010-12-08
The root user is the computer's administrator (to use some windows jargon).
To install the drivers, open a terminal (Applications>Accessories>Terminal)
and navigate to the location where you've saved your drivers, let's say your desktop:
```
cd ~/Desktop
```
Make the file executable:
```
chmod +x filename.run
```
Run the file with root priviledges:
```
sudo ./filename.run
```
You will be asked to provide your password after the last command.
Type it (nothing will appear on screen) and press enter.

---

