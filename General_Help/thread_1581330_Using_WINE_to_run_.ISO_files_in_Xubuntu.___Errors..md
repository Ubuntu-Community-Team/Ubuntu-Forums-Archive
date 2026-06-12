---
title: "Using WINE to run .ISO files in Xubuntu.   Errors."
date: 2010-09-24
forum: General Help
---

### Post by daxbriggs on 2010-09-24
Hello.  I'm trying to install Fallout 1 by Interplay.  I have the .ISO of the game.

I've mounted it to a directory I created (/home/temp), using Gmount

But, when I use the GUI, and right click on the "install.exe" and choose Open With Wine.  It just opens a terminal, than promptly closes it.  

So, I tried to run it in a terminal.  I went to the directory where the ISO is mounted, and used the command

wine install.exe

and it gives me:

err:dosmem:DOSMEM_MapDosLayout Need full access to the first megabyte for DOS mode

Also, when I mount the .ISO using Gmount, I get the error;

An error occured
 Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.

I can also open the autorun.exe using wine.  But when I click the install button in the autorun menu, it says I have to install DirectX.  When I click yes, it gives me the generic windows crash.

"The program your using has encountered a problem and needs to close. yada yada yada."

Choosing 'no' when prompted to install DirectX, just gives me a blank screen, with no response.  

Push ESC three times, and my desktop appears again, and everything is responding.

So, yeah.  

Did I just download a bad .ISO or something?

Or, am I just no good with Linux?

Any help would be appreciated.  Really, been trying to get this game to run for 2 days now.  About ready to just go back to windows...

:(

---

### Post by 7h3d4rk0n3 on 2010-09-24
Try doing:

sudo wine install.exe

and see what happens.

---

### Post by daxbriggs on 2010-09-25
Thank you, Derek.  

But when I ran the wine install.exe command with superuser do, it prompted me for my password, than decided to tell me;

"wine: /home/daxus/.wine is not owned by you"

That's all it said. 

:(

---

### Post by daxbriggs on 2010-09-26
Any more help?

---

### Post by DarthScape on 2010-09-26
DOSBOX!!! have you tried? might work a ton better

---

