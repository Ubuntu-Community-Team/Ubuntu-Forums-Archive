---
title: "Uninstall Ubuntu 10.10 with .exe file."
date: 2010-11-25
forum: General Help
---

### Post by wei2912 on 2010-11-25
I have installed Ubuntu 10.04 using the dvd rom way, then updated it to Ubuntu 10.10. I need to uninstall Ubuntu 10.10 with .exe file. Some help please?

Note: I also need to get rid of the grub boot loader this way.

I just need to uninstall Ubuntu 10.10, then install Kubuntu 10.10.

More info:
I accidentally uninstalled the gnome panel, so i cannot access programs other than opening their files. I also cannot access the internet since after i uninstalled the gnome panel, i could not connect to the internet.

I cannot use the dvd rom, it is outdated (Ubuntu 10.04).

---

### Post by Hippytaff on 2010-11-25
Do you know if you have a Wubi install? did you install it with windows? or did you install it alongside windows?

---

### Post by wei2912 on 2010-11-25
I installed it with the iso file. It is dual boot with windows. It uses the grub boot loader.

---

### Post by dino99 on 2010-11-25
the easy way is to format the partition where ubuntu is installed, if grub is installed elsewhere, first remove/purge grub-pc & grub-common with synaptic

---

### Post by wei2912 on 2010-11-25
But i have a big problem. I have removed the gnome panel, rendering me unable to access synpatic. I cannot create a launcher too. I have to do it in windows.

---

### Post by Hippytaff on 2010-11-25
You can type
```

firefox

``` and it will launch firefox (or the name of whatever browser you use) Also there is a way to restore the panel, but I can't remember off hand, will have to google it :-)

---

### Post by wei2912 on 2010-11-25
> **Hippytaff said:**
> You can type
```

firefox

``` and it will launch firefox (or the name of whatever browser you use) Also there is a way to restore the panel, but I can't remember off hand, will have to google it :-)
Problem is i uninstalled it. In the end, i couldn't connect to the internet, so i had to use windows.

---

### Post by ivarn on 2010-11-25
ok so you want to uninstall ubuntu, then install kubuntu?
Why don't you just do:
sudo apt-get remove ubuntu-desktop && sudo apt-get install kubuntu-desktop.
It's not harder than that.
Also, you said the panels are gone, do this:
sudo apt-get install gnome-panel.

---

### Post by Hippytaff on 2010-11-25
[]("http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/")
 
Missed your edit in the op
 
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install kubuntu-desktop

```
 
As ivan said

---

### Post by wei2912 on 2010-11-25
Notes:
I cannot access the internet - Gnome panel gone, no way to access.
I cannot access the terminal.
I cannot make a launcher.
I cannot use the dvd, it is the Ubuntu 10.04 installation, i just updated ubuntu to 10.10.

Sorry for the misconceptions. I think the only way is to use windows xp.

---

### Post by Yougo on 2010-11-25
when you are at the login screen, press CTRL+ALT+F1

this takes you to a command prompt. you can log in there, and enter above mentioned commands.

when you're done, reboot by typing
```
sudo reboot
```

---

### Post by Hippytaff on 2010-11-25
Also you can open a terminal in Gnome with CTRL+ALT+T

---

### Post by ivarn on 2010-11-25
you can either reboot and do this from recovery mode or while you are in ubuntu, press ALT+F2 This will give you the command line, now type in the command "sudo apt-get install gnome-panel", now when you have the panels you can connect to your internet again. Also, why don't you have internet connection? are you using another computer now that does have internet connection?
Edit, what windows version do you run? If it's windows 7 you also have the Disk Manager application.
You can use that to delete the linux partition. Remember, the partition you want to remove is called ext4.

---

### Post by wei2912 on 2010-11-25
> **ivarn said:**
> you can either reboot and do this from recovery mode or while you are in ubuntu, press ALT+F2 This will give you the command line, now type in the command "sudo apt-get install gnome-panel", now when you have the panels you can connect to your internet again. Also, why don't you have internet connection? are you using another computer now that does have internet connection?
I am using windows xp now, which can connect to the internet. However, in ubuntu 10.10, I have sort of wrecked the thing so i cannot connect to the internet.

Also, is it possible to install the gnome panels without using the internet?

---

### Post by wei2912 on 2010-11-25
Edit: Ignore this message, i don't know why i can't delete it.

---

### Post by dino99 on 2010-11-25
sudo apt-get install ubuntu-desktop

by the way, from xp you can format the ubuntu partition and override grub by reinstalling xp bootloader

[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

---

### Post by wei2912 on 2010-11-25
> **dino99 said:**
> sudo apt-get install ubuntu-desktop
Err... it's uninstall.

---

### Post by Hippytaff on 2010-11-25
> **wei2912 said:**
> I removed:
gnome-panel
gnome-applet
gnome-appletdata (not sure of the name)
 
So will it still work? If yes, i will reboot.
 
Not sure, try it, if not boot into safe mode and drop into a terminal then
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install kubuntu-desktop

```

---

### Post by dino99 on 2010-11-25
look back to post #16

---

### Post by wei2912 on 2010-11-25
I have no recovery disk because i can't find it.

So, is the only way this:
Uninstall ubuntu 10.10, then put in CD for kubuntu 10.10 and install.

---

### Post by ivarn on 2010-11-25
you are going though a lot of stuff now just because your internet configurations are messed up in ubuntu.
If you have a wired internet connection, plug it in, reboot and start the ubuntu recovery mode. Now, you have everything you need in order to do this.
Ok so when you are in recovery mode, you have this list of options, choose "go to root prompt" and type in the commands to repair your system. 
If you don't have a wired internet connection but only a wireless solution, you can't do this from recovery mode. Please tell me if you have a wired or a wireless internet connection and I'll tell you what to do next.

---

### Post by wei2912 on 2010-11-25
I have a wired, but the wire's too short...

---

### Post by ivarn on 2010-11-25
ok login to ubuntu, go to the terminal (CTR+ALT+T) and type in this line:
sudo /etc/init.d/networking restart
This will reset your internet configurations.
Now turn on your wireless internet box, press alt+f2 and type in:
nm-connection-editor
Add your wireless connection here

---

### Post by Swagman on 2010-11-25
To rebuild your top panel do the following after pressing ctrl + alt + T (terminal)

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by wei2912 on 2010-11-25
Thanks for all your help. With the commands, i managed to uninstall ubuntu and install xubunutu (kubuntu seems too complicated to use).

---

### Post by wei2912 on 2010-11-25
Installation failed. I have tried rebooting, then installing, but it didn't work. what is the commnd to fix broken packages? I think i need that.

---

### Post by wei2912 on 2010-11-26
Nvm, problem solved, connected to the internet and it worked. Thanks for all your help.

---

