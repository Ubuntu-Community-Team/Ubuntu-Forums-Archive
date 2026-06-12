---
title: "Start up script"
date: 2011-05-19
forum: General Help
---

### Post by gurulenin on 2011-05-19
Dear Ubuntu friends,

              I am using 3 ubuntu systems connected via LAN.. I have 2 Mbps broadband.. So I am using wondershaper (In terminal : "sudo woundershper eth0 1000 1000 ") to limit the speed whenever i need.. I want to setup start the wondershaper when the system boots.. How to do that ? 

:popcorn:

---

### Post by wildmanne39 on 2011-05-19
> **gurulenin said:**
> Dear Ubuntu friends,

              I am using 3 ubuntu systems connected via LAN.. I have 2 Mbps broadband.. So I am using wondershaper (In terminal : "sudo woundershper eth0 1000 1000 ") to limit the speed whenever i need.. I want to setup start the wondershaper when the system boots.. How to do that ? 

:popcorn:Hi, go into startup apps click add put in the name of the app that you want to auto start where the command box is click browse and find the path of the program that you want to start and put it in there then click the add button make sure it has a check by it and then close. If the program that you want to start needs to start after another program first you will have to add a script to delay it from starting about 30 seconds after boot.

---

### Post by gurulenin on 2011-05-21
> **wildmanne39 said:**
> Hi, go into startup apps click add put in the name of the app that you want to auto start where the command box is click browse and find the path of the program that you want to start and put it in there then click the add button make sure it has a check by it and then close. If the program that you want to start needs to start after another program first you will have to add a script to delay it from starting about 30 seconds after boot.

its ok..

this is the example script..

#!/bin/bash

sudo wondershaper eth0 300 300


here I need root password to run the script.. how to add password to this script..

---

