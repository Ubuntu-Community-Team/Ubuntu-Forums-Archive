---
title: "Display bother"
date: 2009-11-27
forum: General Help
---

### Post by davidU on 2009-11-27
HI,
  I wonder if anyone can tell me how to fix my problem with my display drivers.

I am running Ubuntu 9.04 and have a NVidia GeForce4 Ti 4400 graphics card in my P4 box with a 2.2 GHz CPU, 512 MB RAM.

According to the control panel, I have NVIDIA Driver Version:96.43.10 installed, however, I have to install this each time I boot up.

I tried saving the X Configuration information to /etc/X11/xorg.conf
using the GUI button provided by the NVidia control panel, but this fails with the error message,

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Any ideas how to fix this, please ?

Regards

DavidU:)

---

### Post by fcuk112 on 2009-11-27
i think you can try sudo mv /etc/X11/xorg.conf ~/
to move your xorg.conf (for backup) and then hit the save button.

---

### Post by prshah on 2009-11-27
> **davidU said:**
> 
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Please open the nvidia-settings utility as root to allow the file to be created. Eg, press Alt+F2, and give the command```
gksudo nvidia-settings
``` and press enter to open the utility. Make your settings changes as usual, then choose to save to /etc/X11/xorg.conf.

Please post back if you still have trouble.

---

### Post by davidU on 2009-11-27
> **fcuk112 said:**
> i think you can try sudo mv /etc/X11/xorg.conf ~/
to move your xorg.conf (for backup) and then hit the save button.
Thanks for the advice, unfortunately I got the message, "no such file". However,prshah seemed to have the answer, at least I think the x config file has been saved now.

I'll know when I next boot the machine.

Regards

DavidU

---

### Post by davidU on 2009-11-27
> **prshah said:**
> Please open the nvidia-settings utility as root to allow the file to be created. Eg, press Alt+F2, and give the command```
gksudo nvidia-settings
``` and press enter to open the utility. Make your settings changes as usual, then choose to save to /etc/X11/xorg.conf.

Please post back if you still have trouble.
SOLVED   prshah, it seems you have the answer. at least I think the x config file has been saved now.

I'l know when I next boot the machine.

Regards and thankyou

DavidU

---

### Post by davidU on 2009-11-28
Sorry [prshah]("http://ubuntuforums.org/member.php?u=394709"), that didn't fix anything.

Quite the opposite actually, now I do not have access to the full NVidia software, so I can't change the screen resolution anymore. I am stuck with what looks like an 800 x 600 display but I have no idea, as the GUI control panel has changed so that the options available previously are not evident anymore.

Why is it so damn hard to run Ubuntu ?

DavidU

---

### Post by scouser73 on 2009-11-28
Please follow these instructions for setting up your monitor.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up the monitor to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

---

### Post by davidU on 2009-11-28
Sorry scouser73, that doesn't work.

Something I did yesterday has crippled the GUI for the NVidia control panel. Now there is only one section in  the options tree, but first I have to get rid of the dialogue box that says,

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
It appears to be asking me to do what you just instructed me to do, but I don't know ! 

I saved the config to root by pressing the SAVE button.
But nothing has changed.

Sod is, I only have a BSc in Information Systems and this doesn't seem to be any use when running Ubuntu. Anyways, there is no way to change the screen resolution, or anything else on this cut down control panel.  

The one I had yesterday - before I started giving root commands, would allow me to change the screen resolution etc, BUT I could not save the xconfig file, probably 'cos I didn't use gksudo, but hey, where do I put "gksudo" when there is a graphical button which opens up a Nautilus dialogue, BUT I hadn't got a clue where I am supposed to save the file, or use gksudo.

Still have a crap display.

Why use gksudo, and not just sudo ?

DavidU

---

### Post by scouser73 on 2009-11-28
[[COLOR="Red"]**sudo vs. gksudo**[/COLOR]]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by davidU on 2009-11-28
Thanks scouser73, that explains much, a bit heeeavy mind, but it still went in.

Which leaves me now with another small problem or two.

fcuk112 the other day, told me to 

sudo mv /etc/X11/xorg.conf ~/

which I did using a terminal, (notice the use of "sudo").

Has using "sudo" messed things up ?
Is this why I no longer have the NVidia control panel ?
Where has the NVidia control panel gone ?
How do I get it back ?

Regards

DavidU

---

### Post by prshah on 2009-11-28
> **davidU said:**
> 
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

You don't seem to have the driver installed. Why not try the suggestion in the error message? Press Alt+F2 (or open a Terminal) and give the command ```
gksudo nvidia-xconfig
```, change the settings to your requirement, then restart the X server.

To restart the X server, you can switch to a virtual terminal with Ctrl+Alt+F1, then login, and give the command```
sudo service gdm restart
```

---

### Post by davidU on 2009-11-29
> **prshah said:**
> Please open the nvidia-settings utility as root to allow the file to be created. Eg, press Alt+F2, and give the command```
gksudo nvidia-settings
``` and press enter to open the utility. Make your settings changes as usual, then choose to save to /etc/X11/xorg.conf.

Please post back if you still have trouble.

Sorry mate, that didn't work either.
After Alt+F2 I pasted the command you gave and hit RUN.
I didn't get chance to enter any more commands because my screen greyed out except for a white rectangle in the centre of the screen.
I managed to get the desk top back by pressing Esc.

Now what !

It doesn't help that I have a damn job navigating this messaging environment.
I pasted your commands into the message and now have two boxes with code, which I don't want and canot delete or remove from this message !

SHEESH I am struggling here.

Managed to delete the unwanted code thankfully, this is a nightmare !

---

### Post by davidU on 2009-11-29
fcuk112, I don't fully understand what happened when I followed your advice.
I think you instructed me to back up the existing xorg.conf file.

Which was a good start.
However, I now have no access to the  NVidia control panel, the one I used to change my settings after each fresh boot.

Sorry I am such a pratt, they didn't teach me **** all about Linux when I got my degree. It was all done on Microsoft Windows !!!!

---

### Post by davidU on 2009-11-30
Hi, just to update regarding my display bother.

At boot this morning, the OS went into a check for installed drivers.
The result is that I now have more parts of the NVidia control panel back and accessible so I can change the resolution to 1240 x 960. BUT I still cannot save the new configuration even if I type gksudo before it

However, the bit which controls the size and position of the window is missing !

More bits missing are the minimise, maximise and close buttons from all the applications I've been running, Epiphany, Firefox, Seamonkey, Bluefish, Tomboy Notes, Solitaire !  Open Office has the close button ONLY.

Every one of these apps has lost those icons from the top right corner of the screen.

SHEESH !

This is pure agony - Ubuntu 9.04 is RUBBISH....... 
It is no good as a production environment for a business, where do you people get the idea that it is ?

DavidU

---

