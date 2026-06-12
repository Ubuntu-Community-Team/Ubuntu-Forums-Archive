---
title: "Networking Problem"
date: 2009-07-18
forum: General Help
---

### Post by Tman5293 on 2009-07-18
Hi,

I have a small problem with my network. When I go to Places and click Network all thats in there is "Windows Network." But this not my problem. My problem is that when I click "Windows Network" all I get is an error that states:

Unable To Mount Location
Failed to retrieve share list from server

Can someone please help me with this problem???

BTW my network consists of 1 Ubuntu computer and 2 Vistas and I would like to be able to access shared files on the 2 Vistas from my Ubuntu computer and vice versa.

---

### Post by Tman5293 on 2009-07-18
Nobody can help me???  :(

---

### Post by doas777 on 2009-07-18
well it may be an authentication issue. 

first, is samba isntalled? you can install it from synaptic or add remove, or from the terminal with ```
sudo apt-get install samba
```
with samba installed, hit Alt + F2, and paste in:
```
gksu gedit /etc/samba/smb.conf
``` add the line:
```
client NTLMv2 auth = yes
```then you can either reboot, or you can restart samba from a terminal with:
```
sudo /etc/init.d/samba restart
```also find the line that starts with "**workgroup =**" and make sure that you are in the correct workgroup with your wintel boxen.
save teh file and exit gedit.

after that, hopefully you will be asked for a password when browsing to a machine.

---

### Post by Tman5293 on 2009-07-18
> **doas777 said:**
> well it may be an authentication issue. 

first, is samba isntalled? you can install it from synaptic or add remove, or from the terminal with ```
sudo apt-get install samba
```with samba installed, hit Alt + F2, and paste in:
```
gksu gedit /etc/samba/smb.conf
``` add the line:
```
client NTLMv2 auth = yes
```then you can either reboot, or you can restart samba from a terminal with:
```
sudo /etc/init.d/samba restart
```also find the line that starts with "**workgroup =**" and make sure that you are in the correct workgroup with your wintel boxen.
save teh file and exit gedit.

after that, hopefully you will be asked for a password when browsing to a machine.

This didnt work for me i still get the same error when I try to go to "Windows Network"

And what is "wintel boxen" ???

---

### Post by doas777 on 2009-07-18
> **Tman5293 said:**
> This didnt work for me i still get the same error when I try to go to "Windows Network"

And what is "wintel boxen" ???

sorry it didn't work for ya.

windows PCs. "wintel" is a throwback to the time when all consumer PCs were Windows/Intel or Mac/Motorola. "Boxen" is an improper plural for boxes (slang for PC towers), in the same form as ox -> oxen.

---

### Post by Tman5293 on 2009-07-18
Does anyone know why my computer fails to retrieve share list from server????

---

### Post by Tman5293 on 2009-07-18
Someone please find a working answer!!!! I really want to be able to share files between Ubuntu and Vista.

---

### Post by 3rdalbum on 2009-07-18
Have you tried using the System-config-samba program (from the repositories) to set up Samba on the Ubuntu machine? It's a lot easier to set up.

Funnily enough I had this problem today - Gnome gave me the same error messages. So I typed this into the address bar in Nautilus:

```
smb://192.168.0.12
```

That's the IP address of my server. Obviously, you'd replace that with the local IP address of your Vista server. This will always get you to your share.

I don't know what causes Gnome to give that error message when the share is definitely there, but it seems to get better on its own.

---

### Post by Tman5293 on 2009-07-19
> **3rdalbum said:**
> Have you tried using the System-config-samba program (from the repositories) to set up Samba on the Ubuntu machine? It's a lot easier to set up.

Funnily enough I had this problem today - Gnome gave me the same error messages. So I typed this into the address bar in Nautilus:

```
smb://192.168.0.12
```That's the IP address of my server. Obviously, you'd replace that with the local IP address of your Vista server. This will always get you to your share.

I don't know what causes Gnome to give that error message when the share is definitely there, but it seems to get better on its own.

Thank this worked. But for some reason I still cant find my Ubuntu computer on my Vista computers.  :confused:

---

