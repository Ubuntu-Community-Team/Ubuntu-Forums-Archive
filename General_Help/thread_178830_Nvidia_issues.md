---
title: "Nvidia issues"
date: 2006-05-18
forum: General Help
---

### Post by Dr_Deadmeat on 2006-05-18
I have issues with my nvidia card (Nvidia GeForce 420 go) on my laptop and my last stunt to get it to work with 3d destroyed it almost completely... I am going to do a clean install of Kubuntu 6.06 if I don't get an answer within 20 minutes... Please help me, I've got much data in there that I really don't want to lose :( 

Please

---

### Post by Ramses de Norre on 2006-05-18
Hmm maybe you can be a little more specific then 'I have issues'
Describe the problem so we know what exactely doesn't work, and give the error messages.

---

### Post by Dr_Deadmeat on 2006-05-18
[QUOTE=Ramses de Norre]Hmm maybe you can be a little more specific then 'I have issues'
Describe the problem so we know what exactely doesn't work, and give the error messages.[/QUOTE]

Ok.. I am sorry, but I am a bit stressed... My issues is that I only got 640x480 in ressolution, and when I tries to change it, I cant start gnome anymore... Please help me

---

### Post by Dr_Deadmeat on 2006-05-18
I'd gave up, and now I soon have Kubuntu 6.06 =D (I hope that give me better results with 3d acceleration on my card)

---

### Post by dg_w on 2006-05-18
rearlt it could not be easier for nvidia

Make sure you have all the repos un commented in /etc/apt/sources.list
 sudo apt-get update
 sudo apt-get dist-upgrade

then to install nvidia

sudo apt-get install nvidia-glx nvidia-kernel-common

then:

sudo gedit /etc/X11/xorg.conf
Find this section 
...
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"


change to read

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0" 


save and reboot thats it .... rearly :)

---

