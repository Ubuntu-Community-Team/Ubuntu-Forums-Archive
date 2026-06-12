---
title: "Grub 2 configuration"
date: 2010-05-12
forum: General Help
---

### Post by frankiethepill on 2010-05-12
Is there, or is there likely to be, a configuration program for Grub 2? I have always found Grub to be a major problem to deal with, and Grub 2 is an absolute nightmare to sort out. Startup Manager does some things but not a lot. 
Every time we have an update we get a new kernel revision and yet another entry on the grub startup menu (getting quite long now) - how do I get rid of the excess entries and can I make the default startup option (in my case Windows, sorry but necessary for my business) as each time we get an update I lose the default.

---

### Post by cbecker78 on 2010-05-12
Look at this post for basics of grub2

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

getting rid of old kernels should be an option in the disk janitor, or through synaptic.  I used the disk janitor in the past.

To set the default os :

run "gksudo gedit /etc/default/grub"  and change the value of GRUB_DEFAULT to the number of the menu item in grub.  Remember to start counting from zero, and remember to run "sudo update-grub" when you are done.

From the linked post:
**GRUB_DEFAULT**  - Sets the default menu entry. Entries may be numeric or "saved"
[LIST]
[*]**GRUB_DEFAULT=0**  - Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" is 0, the second is 1, etc.
[/LIST]

---

### Post by Alan F on 2010-05-12
Startup Manager will set Windows to default OS

Remove the old kernels with Synaptic

Here
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

tells you how to get rid of Memtest and Recovery mode options

Yes, I agree with you, a good version of Startup Manager is required for Grub2

---

