---
title: "Installing a Program through the Terminal"
date: 2011-07-07
forum: General Help
---

### Post by El3mentGamer on 2011-07-07
I'm trying to install a program through the terminal and im getting an error that im not quite understanding.

I'm running Ubuntu 11.04 Natt Narwhal. 

Here is the read-me file:
> Shrewd's Crafty GUI v.25b for MineCraft
---------------------------------------

*****************************************************
*** VERY IMPORTANT FOR NEW FEATURE: MOD INSTALLER ***
*****************************************************

All mods to be installed by Shrewd's Crafty GUI must follow these guidelines:

a) must be a zip archive
b) the directory structure of the mod zip archive must match the end result to work in the minecraft.jar file

For example, if you have a mod file named MyMod.zip which has class files located in MyMod/Class/*.class then it will not work. They must reside in the main directory of MyMod.zip.  If you are not sure if it will work, ask me and I can let you know.

Backups of your original minecraft.jar file will be date and time stamped and put in ./minecraft/bin/minecraft_backups should you need to restore do to a conflict or something.

------

Minecraft is Copyright by Mojang AB @ [www.minecraft.net]("http://www.minecraft.net")

Shrewd's Crafty GUI is Copyright 2011 by Christopher Hoyer - Shrewd

Shrewd's Crafty GUI is in no way affiliated with the game Minecraft or Mojang AB. This program is intended to make the installation easier on the linux operating system...

Minecraft and Minecraft server require Java to be installed.

To install java, at terminal command prompt enter:

sudo apt-get install sun-java6-jre sun-java6-plugin

Please make sure these are install before using this program.

sudo apt-get install kommander-kde3 gksu fastjar

To install, goto the directory you placed 'Shrewd's Crafty GUI' in and at terminal command prompt:

sudo ./setup.sh' from terminalI've installed the java and kommander both.

When i type in the "sudo ./setup.sh" code in a new-opened terminal i get this error.
> brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo ./setup.sh
[sudo] password for brandon: 
sudo: ./setup.sh: command not foundWhen i type the code in a the setup.sh terminal popup i get this error.
> @----------------------------------------@
@      Shrewd's Crafty GUI Setup         @
@            Version .10a                @
@----------------------------------------@


What would you like to do?

1. Install Shrewd's Crafty GUI
2. Uninstall Shrewd's Crafty GUI
3. Exit
sudo ./setup.sh
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 132: [: too many arguments
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 137: [: too many arguments
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 142: [: too many arguments
Invalid choice
a

What am i doing wrong? How do i fix it >:(

---

### Post by searchfgold6789 on 2011-07-07
Try this:
```
sudo bash ./setup.sh
```
Or this:
```
sudo su
./setup.sh
```

---

### Post by El3mentGamer on 2011-07-07
neither of them worked :(

---

### Post by El3mentGamer on 2011-07-08
BUMP!:guitar:

---

