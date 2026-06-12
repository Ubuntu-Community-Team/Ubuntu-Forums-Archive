---
title: "Computer now boots to command line"
date: 2012-09-03
forum: General Help
---

### Post by DarrylLicke on 2012-09-03
I just installed Ubuntu 12.04 LTS for this new box and after updating all the software it now boots to the command line.  I can get to the desktop just fine by logging in and typing xstart but I'd rather not do that if possible. Any suggestions?

---

### Post by 73ckn797 on 2012-09-03
> **DarrylLicke said:**
> I just installed Ubuntu 12.04 LTS for this new box and after updating all the software it now boots to the command line.  I can get to the desktop just fine by logging in and typing xstart but I'd rather not do that if possible. Any suggestions?

Were there any other tweaks made during or after the updates?

Do you not get the Grub menu?

---

### Post by opensshd on 2012-09-03
try putting:

exec gnome-session

in your ~/.xinitrc

If you don't have that, create it and try that?

---

### Post by Sanitylost on 2012-09-04
Hey,

did you try to run the install for the nvidia drivers? If so i ran into a similar problem try this.

```
sudo apt-get install gdm


```

then. after running the install, select gdm as the default display manager. This should get you back up and running after a reboot. Now

```
 sudo apt-get purge lightdm
sudo apt-get remove lightdm
sudo apt-get autoremove
sudo apt-get install lightdm

```

This fixed my problem and brought my display back to its original status. Hope this helps.

---

### Post by DarrylLicke on 2012-09-08
Here's what I did to get where I'm at now: I downloaded boot repair and ran it.

What it did I don't know but now I'm at a point where I think it boots into GRUB and lets me select whether I want one of two ubuntus (regular and recovery) and two memory tests.

I'd like to get it to the point where it just boots into regular ubuntu but at least now I don't have to run xstart after logging in.

---

