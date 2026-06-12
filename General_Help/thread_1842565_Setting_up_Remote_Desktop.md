---
title: "Setting up Remote Desktop"
date: 2011-09-11
forum: General Help
---

### Post by grinkle on 2011-09-11
I have two computers one rebuild (gigabyte E350N motherboard AMD E-350 processor, 8GB DDR3, vertex2 SSD, 2TB HDD Gb Ethernet) running Ultimate 2.9
The other one is an old one (ASRock K7S41 motherboard, AMD Sempron 2600 processor, 512MB DDR, 20GB HDD10/100 Ethernet) running Bhodi Linux (I can add a faster ethernet card if i need it)
I would like to run the desktop on both machines from the newer one. there are 6 accounts so i would like to be able to start the old machine so i get the login screen from the new one or create a similar one that starts and runs the accounts on the other machine.
I looked at running terminal server and thought that might be over kill
i tried VNC but can only view the remote desktop that is running (I checked the settings) but I cant get it to interact
I tried SSH (I think) That got me a prompt
The answer is probably simple but the more i read the more confused I get
I am open to suggestions of the best way to tackle this but please spell it out simply for me and other new users

---

### Post by haqking on 2011-09-11
> **grinkle said:**
> I have two computers one rebuild (gigabyte E350N motherboard AMD E-350 processor, 8GB DDR3, vertex2 SSD, 2TB HDD Gb Ethernet) running Ultimate 2.9
The other one is an old one (ASRock K7S41 motherboard, AMD Sempron 2600 processor, 512MB DDR, 20GB HDD10/100 Ethernet) running Bhodi Linux (I can add a faster ethernet card if i need it)
I would like to run the desktop on both machines from the newer one. there are 6 accounts so i would like to be able to start the old machine so i get the login screen from the new one or create a similar one that starts and runs the accounts on the other machine.
I looked at running terminal server and thought that might be over kill
i tried VNC but can only view the remote desktop that is running (I checked the settings) but I cant get it to interact
I tried SSH (I think) That got me a prompt
The answer is probably simple but the more i read the more confused I get
I am open to suggestions of the best way to tackle this but please spell it out simply for me and other new users


use SSH it is the most secure.

and use something like

ssh -X username@ip

the -X will allow you to run graphically, X uses loopback netwokring so you can run remote graphical apps using the local X server.

Can be a little slow though

RDP uses VNC in linux so though the initial connection is encrypted any data after that is sent in clear text

---

### Post by grinkle on 2011-09-11
Thanks for the help
I will try it and post back what append for others

---

### Post by haqking on 2011-09-11
> **grinkle said:**
> Thanks for the help
I will try it and post back what append for others


no problem, hope it helps.

post back with any issues.

remember when you login with ssh -X, it will still be CLI until you invoke a GUI command such as gksudo gedit for example.

gedit will open locally on your machine and before doing so will ask for admin privelge cos you specified gksudo, you enter the remote accounts password remember not your local one.  and when you save the document it is saving to the remote filesystem as X is running locally on your machine on behalf of the remote X, does that make sense ?

play with it a little and it will make sense.  Locally speed wont be an issue, if you plan the ssh -X across a wan then it may appear slow at times

Cheers

---

