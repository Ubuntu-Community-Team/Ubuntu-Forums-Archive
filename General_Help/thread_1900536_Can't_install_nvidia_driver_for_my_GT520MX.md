---
title: "Can't install nvidia driver for my GT520MX"
date: 2011-12-26
forum: General Help
---

### Post by choallin on 2011-12-26
Hi there!

I've downloaded the correct driver for my graphic card (a nvidia GT520MX) from the nvidia website. If I want to install it in the terminal, I get the message I have to shutdown the X-Server first. Unfortunately I don't know how... . How do I do this with unity?
Also, I'm wondering why I don't get a suggestion in systemsettings --> additional drivers. It says there that I'm not useing propritary drivers (which I perfectly know) but it also don't offers me one to install for my graphic card. Therefore I've looked into the software-center, searched for nvidea and tried to install one of those. But, I can't because I get the message that there is no software package called nvideal-glx-185 in my software sources... .
Does someone know what to do?

---

### Post by Bobhuber on 2011-12-26
First save the nvidia.run file so you know where it is or leave it in your Downloads directory and mark it as executable. I usually rename the file to nvidia.run to make things easier from a terminal.
I'm going to give you the easiest way.

First >  To prevent any problems installing the driver edit the /etc/modprobe.d/blacklist.conf file and add the following lines to the end of the file.

blacklist nouveau
 options nouveau modeset=0

Reboot in the safe mode (recovery mode from the grub menu). Select normal boot from the pop up menu.
You will be at a terminal prompt now before the xserver loads
 Login with your user name and password. 
Change to the directory that contains your nvidia.run file  ( cd /home/bob/Downloads)
sudo sh ./nvidia.run

 Good Luck

---

### Post by choallin on 2011-12-26
Thanks for your answer. But unfortunately I don't know how to start in safe mode... .
I've just Ubuntu running on my PC, therefore I don't get the grub menu which OS I want to start. What should I do to restart in safe mode?

---

### Post by Bobhuber on 2011-12-26
> **choallin said:**
> Thanks for your answer. But unfortunately I don't know how to start in safe mode... .
I've just Ubuntu running on my PC, therefore I don't get the grub menu which OS I want to start. What should I do to restart in safe mode?
OK - Blacklist nouveau as instructed.

CTRL+ALT+F1 will bring you to a terminal.

Login with your user name and password.

Change to the directory that contains the nvidia run file. Stop the xserver.

sudo stop lightdm

sudo sh ./nvidia.run

---

### Post by Bobhuber on 2011-12-27
Sorry I forgot that the blacklist won't work if you go from the op system. Hold the shift key down during boot to get to the grub menu and recovery mode.

---

### Post by vangop on 2011-12-27
I'd try to use the "additional drivers" applet first. 
The reason it's not showing you any suggestions could be that you don't have restricted repositories enabled. Run synaptic->settings->repositories and mark all the checkboxes.
The reload and try the drivers applet again.

---

### Post by choallin on 2011-12-28
Thanks for your help, I've installed the nvidea driver. How do I check if it is working correctly? Because I think it isn't working as intended... .

---

### Post by choallin on 2011-12-29
I've done a little bit research now, and now I'm 100 % sure that the driver isn't working. Unfortunately I can't say why it's not working... . How can I fix that? Or, how can I find out what's broken?
I'm open for any suggestion.

so long
choallin

---

