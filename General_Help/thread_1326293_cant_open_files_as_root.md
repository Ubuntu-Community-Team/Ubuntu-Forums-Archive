---
title: "cant open files as root"
date: 2009-11-14
forum: General Help
---

### Post by zaphodbblx on 2009-11-14
OK I'm trying to change my grub 2 splash screen BUT to do that i have to move the images from "grub" to "desktop-base" BUT when i try to move files it says I don't have privileges to do it 
heres what I've tried:
1) Create a gksudo Launcher

    * Right-click unused space in either the top or bottom panel.
    * Choose “Add To Panel…”
    * Choose Custom Application Launcher
    * In the window that pops up, enter the following:
      Name: GKSudo launcher
      Command: gksudo “gnome-open %u”
      Comment: Open files with root privilege
    * Click the No Icon button to select an icon for your launcher.
    * Click OK

Your Gksudo launcher should now appear on the panel.

Now, to open a file with root privilege, just drag and drop the file to this launcher.

2) Install ‘nautilus-gksu’

Install ‘nautilus-gksu‘ via the Synaptic Package Manager. Now when you right click on any files or folder, you can see the option “Open as administrator“.

3) Use nautilus-script

If for some reason, you can’t install the ‘nautilus-gksu‘, you can achieve the same function via creating a nautilus script manually.

In the terminal,

gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ Administrator

Insert the following lines into the new file:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do gksudo “gnome-open $uri” & done

Save the file.

Make the file executable:

chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ Administrator

You can now open files as root by right clicking on the file and selecting Scripts->Open as Administrator

not a biggie but I hate the loss of control I'm feeling right now....

Gosh guys Linux Mint has a menu option in right click(open as root) why don't we?

---

### Post by scouser73 on 2009-11-14
For Root privileges you need to enter this command into **Terminal**

> **gksudo nautilus**

[COLOR="Red"]**Please be very careful when using Root as you can potentially damage your system if you don't know what you are doing.**[/COLOR]

---

### Post by ciprian.topala on 2009-11-14
a simpler solution would be using Ubuntu Tweak.
under the Personal menu, in the Scripts submenu there is a nautilus script called Browse as root which does exactly the same thing zaphodbblx described in the first post.

---

### Post by cmcanulty on 2009-11-14
How do you do it? I found the browse as root but then the only option is rebuild scrips, do I check that?

---

### Post by oldos2er on 2009-11-14
> **zaphodbblx said:**
> OK I'm trying to change my grub 2 splash screen BUT to do that i have to move the images from "grub" to "desktop-base" BUT when i try to move files it says I don't have privileges to do it 
heres what I've tried:
 Install ‘nautilus-gksu’

Install ‘nautilus-gksu‘ via the Synaptic Package Manager. Now when you right click on any files or folder, you can see the option “Open as administrator“.


 After installing nautilus-gksu, you need to either reboot or restart X to enable it.

---

### Post by zaphodbblx on 2009-11-14
> **oldos2er said:**
> After installing nautilus-gksu, you need to either reboot or restart X to enable it.

ahhh That make tons of sense
thanks!

OK on the same topic I dual boot with mint and its my primary desktop now but Ubuntu comes up first in grub, could that be why changing grub in mint didn't do the changes?
thanks all and I promise I'll be careful with root ;)

---

### Post by oldos2er on 2009-11-14
Yes, if Ubuntu's /boot/grub is the one the MBR points to, you'll have to edit it instead of Mint's.

---

### Post by ciprian.topala on 2009-11-15
> How do you do it? I found the browse as root but then the only option is rebuild scrips, do I check that?

you have to drag the Browse as root script from disabled scripts (the right side of the screen) to enabled scripts (the left side of the screen)

---

### Post by zaphodbblx on 2009-11-15
was this set up different than jaunty for a fresh install?  honestly I'm not sure because I think this is the first time I've moved anything in the file system.
thanks for the good intel guys

---

