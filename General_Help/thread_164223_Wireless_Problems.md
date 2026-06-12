---
title: "Wireless Problems"
date: 2006-04-22
forum: General Help
---

### Post by adnaann on 2006-04-22
I GOT IBM T42 AND I INSTALLED UBUNTU ON IT  MY LAN CARD IS WORKING OUT OF BOX BUT I GOT SERIOUS PROBLEMS WITH MY WIRELESS CARD 
I INSTALLED  network-manager  THE PROBLEM IS THAT IT DONT SHOWS THE 
64BIT ENCRYPTION IN THE TABS , AND AS 64BIT ENCRYPTED KEY IS USED ON MY OFFICE NETWORK  AND I GOOOGLED ALOT BUT CANT FIND ANY THING ABOUT HOW TO CHANGE YOUR ENCRYPTION FROM 128 BIT TO 64BIT  AS I GUESS THATS THE ONLY THING KEEPIN ME DISSCONNECTED 

ANYBODY KNOWS HOW TO DO IT ??

---

### Post by Ramses de Norre on 2006-04-22
sudo gedit /etc/network/interfaces
Insert a line ```
wireless-key 3D#BA#26EE

``` in the section of the wireless device (section starts with line iface eth1 ... if eth1 is the wireless)
Fill in the correct code and don't mind the 64 or 128bit thing (it figures it out itself).

---

