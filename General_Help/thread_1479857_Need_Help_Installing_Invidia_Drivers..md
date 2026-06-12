---
title: "Need Help Installing Invidia Drivers."
date: 2010-05-11
forum: General Help
---

### Post by kornfan on 2010-05-11
First i am new to Linux so i know absolutely nothing about it. I need help installing drivers for a new invidia graphics card. the following is the error message i receive after i have downloaded the current drivers for this card.

Could not open the file /home/linuxuser/Desktop/…ux-x86-195.36.24-pkg1.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

The Invidia website gave instructions on how to go about installing the drivers however they are geared toward a more experienced user than myself. If you need more info plz let me know and how to go about finding it. 

I do know that this computer is using Ubuntu (don't know what version) with the Gnome environment. The graphics card is the Nvidia geforce 210. I have downloaded the 32 bit drivers for the card. 

Thank you in advance for any and all help that can be given.

---

### Post by WorMzy on 2010-05-11
First of all, why are you downloading the drivers from the nVidia site? Do you have a specific reason, or did you not know that you can get the drivers from the various program managers installed on Ubuntu?

[LIST=1]
[*]If you open Software Centre (Applications -> Ubuntu Software Centre), and search for "nVidia-current" (no quotes), you can install the drivers there.

_**OR**_


[*]If you open Synaptic (System -> Administration -> Synaptic Package Manager), search for "nVidia-current" (again, no quotes), you can install the drivers there.

_**OR**_


[*]If you open a terminal (Application -> Accessories -> Terminal), you can install the drivers with the following command:
```
sudo apt-get install nvidia-current
```

_**OR**_


[*]If you want to proceed with the .run file, you need to open a terminal (Application -> Accessories -> Terminal), browse to the folder you downloaded it to with
```
ls /path/to/folder
```
Then make the .run exectuable with
```
chmod +x the-files-name-here.run
```
Then execute it with
```
./the-files-name-here.run
```
[/LIST]

---

### Post by ceedub7 on 2010-05-11
You may need to allow restricted software before following WorMzy's steps. Restricted software is proprietary software not released under a free license. It will still be free to download and use.

Go to System>Administration>Software Sources and click on the checkbox that says 'Software restricted by copyright or legal issues (multiverse)'.

The reason you got an error from Gedit is that Ubuntu was trying to display the file rather than run it. This is because it wasn't set to be run as an executable. 

The step WorMzy described that involved 'chmod' marks it as an executable file. Alternately it can be done graphically by right clicking on the file, clicking on 'Properties' and then going to the 'Permissions' tab. There is a checkbox which says 'Allow execution of file as program'. In this case, however, I would just skip it and go with the 3rd option WorMzy listed to install your driver. I have a Nvidia card and that's how I did it. 

Gedit is just a text editor. It is (roughly) comparable to WordPad on Windows.

If you are new and coming from Windows it is possible that using the terminal to do things can be intimidating. My advice is to try to learn how to do things with the terminal whenever possible, even if a graphical alternative is offered. Eventually you will find it easier to do many things with the terminal than with the graphical alternatives.

---

