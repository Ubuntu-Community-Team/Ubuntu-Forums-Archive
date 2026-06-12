---
title: "Gnome power management help"
date: 2010-10-01
forum: General Help
---

### Post by chipinga on 2010-10-01
Hoping someone can help me with some guidance.

I have a "stripped down" version of ubuntu 9.10 that was created for me by a developer.

It's installed on a Dell Latitude 2100 and I have a flash drive with an image so that I can install it onto multiple Dell Latitude 2100's to use out in the field.

The original developer is no longer able to support the software and I have a problem with the gnome power manager (I think that's where the problem is) in that when lid is closed, I get a black screen.

I know that the laptop is still running fine behind this black screen because if I plug in an external monitor I can see the screen (only on the external) and use the laptop fine.

I know also that the developer stripped out parts of the gnome power manager and possibly acpi as well (if that has anything to do with the lid switch?)

I can get the screen back if I go to a terminal and "sudo vbetool dpms on". I do this by using the external monitor but this doesn't solve my issue because out in the field there is no external monitor to use. The lid gets closed often in the field ad the only way to get it back is to hard reboot (hold down the power button till power off and then turn it on again.

I've tried removing and re-installing gnome power manager as well as acpi and acpi support but this doesn't help.

I've tried using gconf-editor to set the lid_ac and lid_battery to "blank" and also "nothing" and I still get the same problem.

When installing a full copy of 9.10 on these laptops and setting the lid_ac and lid_battery settings to "blank" or "nothing" it works perfectly so it's definitely something to do with what's been stripped out.

At this stage, I am just looking for a solution that will allow people out in the field to get the screen back on whenever this happens ... so even if it's a case of them being able to invoke the "sudo vbetool dpms on" command by some manner ... note that part of the stripping has been to disable various key bindings.

I hope someone can help?

---

### Post by dino99 on 2010-10-01
better support in this subforum:

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

check installation and config:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by chipinga on 2010-10-01
Thanks dino99

I saw that sub forum but since it wasn't specifically a problem with the dell machine (with the full install it all works perfectly) I thought the general forum was better.

I ran those commands but no updates were needed and nothing installed ... should I have seen anything specific there?

---

