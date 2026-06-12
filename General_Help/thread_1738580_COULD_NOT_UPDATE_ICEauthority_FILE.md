---
title: "COULD NOT UPDATE ICEauthority FILE"
date: 2011-04-24
forum: General Help
---

### Post by nickman1122 on 2011-04-24
So when i boot on ubuntu, i get the error  "Could not update ICEauthority file /var/lib/gdm/.ICEauthority" When I close the error, it shows the normal login screen, but i cant choose my user because it does not show any user being there. Also, i go to the power menu(the button to restart and shut down at the bottom right) and i click restart, but it does nothing. Im running dual boot with Ubuntu 10.10 and Windows 7(if thats related)
Please help. thanks

---

### Post by Krytarik on 2011-04-25
Try this for a start:
- at the login screen, press Ctrl+Alt+F1 to switch to a console
- login there
- make sure that everything inside "/var/lib/gdm" is owned by "gdm":
```
sudo chown gdm.gdm -R /var/lib/gdm
```- make sure that "/var/lib/gdm/.ICEauthority" has the correct permissions:
```
sudo chmod 600 /var/lib/gdm/.ICEauthority
```- restart GDM:
```
sudo service gdm restart
```Greetings.

---

### Post by hawk_egus on 2011-05-25
> **Krytarik said:**
> Try this for a start:
- at the login screen, press Ctrl+Alt+F1 to switch to a console
- login there
- make sure that everything inside "/var/lib/gdm" is owned by "gdm":
```
sudo chown gdm.gdm -R /var/lib/gdm
```- make sure that "/var/lib/gdm/.ICEauthority" has the correct permissions:
```
sudo chmod 600 /var/lib/gdm/.ICEauthority
```- restart GDM:
```
sudo service gdm restart
```Greetings.


thanx this solve problem

---

### Post by alfirin on 2011-05-29
Still doesn't work for me :(

---

### Post by luxiaotong on 2012-02-04
> **Krytarik said:**
> Try this for a start:
- at the login screen, press Ctrl+Alt+F1 to switch to a console
- login there
- make sure that everything inside "/var/lib/gdm" is owned by "gdm":
```
sudo chown gdm.gdm -R /var/lib/gdm
```- make sure that "/var/lib/gdm/.ICEauthority" has the correct permissions:
```
sudo chmod 600 /var/lib/gdm/.ICEauthority
```- restart GDM:
```
sudo service gdm restart
```Greetings.
thx solved my problem

---

