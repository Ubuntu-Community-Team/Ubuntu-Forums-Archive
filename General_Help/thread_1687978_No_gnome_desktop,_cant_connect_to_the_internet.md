---
title: "No gnome desktop, cant connect to the internet"
date: 2011-02-14
forum: General Help
---

### Post by lumunofloginism on 2011-02-14
I accidentally deleted the gnome desktop while trying to configure a wireless adapter.
and without a menu i dont know how to make my computer use the wired connection.

im utterly stuck.

---

### Post by cam3roon on 2011-02-14
do you have the livecd?

---

### Post by Azyx on 2011-02-14
> **lumunofloginism said:**
> I accidentally deleted the gnome desktop while trying to configure a wireless adapter.
and without a menu i dont know how to make my computer use the wired connection.

im utterly stuck.

Can you right-click on the meny and select Add to Panel... and the choose NetworkManager Applet 0.8  ?

---

### Post by lumunofloginism on 2011-02-14
> **cam3roon said:**
> do you have the livecd?

i have the cd i made for the boot disk.
but when i get to the part where it says install it just sits there with the loading icon.

---

### Post by lumunofloginism on 2011-02-14
> **Azyx said:**
> Can you right-click on the meny and select Add to Panel... and the choose NetworkManager Applet 0.8  ?

well what i ment was that i deleted the menu from my desktop.
i uninstalled gnome something or other

---

### Post by chili555 on 2011-02-15
Open a terminal and do:```
sudo dhclient eth0
```Does it connect or time out? You might also drop the Ubuntu CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install gnome-desktop
```Of course, it will complain if it can't find the on-line repositories, but it should grab the packages from the CD. Post back and let us know your progress.

---

### Post by lumunofloginism on 2011-02-15
> **chili555 said:**
> Open a terminal and do:```
sudo dhclient eth0
```Does it connect or time out? You might also drop the Ubuntu CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install gnome-desktop
```Of course, it will complain if it can't find the on-line repositories, but it should grab the packages from the CD. Post back and let us know your progress.

i did all of it, and on the last part it said,
( E: unable to lacate package gnome-desktop

---

### Post by lumunofloginism on 2011-02-15
> **chili555 said:**
> Open a terminal and do:```
sudo dhclient eth0
```Does it connect or time out? You might also drop the Ubuntu CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install gnome-desktop
```Of course, it will complain if it can't find the on-line repositories, but it should grab the packages from the CD. Post back and let us know your progress.

well actually, i just tried the first part, and it connects me and im able to use firefox..
but if i restart the computer and go straight to firefox it doesnt work

---

### Post by PaulReaver on 2011-02-15
i think you mean "sudo apt-get install ubuntu-desktop"

---

### Post by lumunofloginism on 2011-02-15
> **PaulReaver said:**
> i think you mean "sudo apt-get install ubuntu-desktop"
it says that it cant get a lock on it

---

### Post by chili555 on 2011-02-15
> **PaulReaver said:**
> i think you mean "sudo apt-get install ubuntu-desktop"Quite correct; sorry about that. If you can go on line, please do:```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```> it says that it cant get a lock on itDo you have Synaptic or Update Manager open? Please close them and proceed.

---

### Post by dbzkid on 2011-10-08
> **chili555 said:**
> Open a terminal and do:```
sudo dhclient eth0
```Does it connect or time out? You might also drop the Ubuntu CD in the tray and try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install gnome-desktop
```Of course, it will complain if it can't find the on-line repositories, but it should grab the packages from the CD. Post back and let us know your progress.
I found my self in the same position as the OP. To get my network back on I needed to remove network-manager
```
sudo apt-get remove network-manager
```
once I did that I was able to do
```
sudo iwconfig wlan0 essid NETWORK_NAME
sudo dhclient wlan0
```
Then all of a sudden I was able to ping :D...
As of now I am going to reinstall my UI. Hope this helps!

---

