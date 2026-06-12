---
title: "Boot Options Manger"
date: 2012-08-03
forum: General Help
---

### Post by tecknomage on 2012-08-03
**RE**: Ubuntu 12.04, GNOME Classic Desktop

Where is the manager for the boot/login options :confused: (*Ubuntu, GNOME ..., etc*)

I need to remove some boot options.

---

### Post by Dylan1473 on 2012-08-03
I don't know if there is a graphical manager included with Ubuntu but a cursory search reveals something called Grub-Customizer seems to be popular. _[Here's]("http://www.unixmen.com/grub-customizer-2-5-5-is-available-customize-grubburg-from-a-gui-interface/")_ a link to an installation guide.

EDIT: Just used it to change the grub background image and it works okay.

---

### Post by tecknomage on 2012-08-04
> **Dylan1473 said:**
> I don't know if there is a graphical manager included with Ubuntu but a cursory search reveals something called Grub-Customizer seems to be popular. _[Here's]("http://www.unixmen.com/grub-customizer-2-5-5-is-available-customize-grubburg-from-a-gui-interface/")_ a link to an installation guide.

EDIT: Just used it to change the grub background image and it works okay.

You misunderstood, I'm talking about t post-Grub. **I want to remove some of the desktop options at the Ubuntu login.**

Thanks anyway :neutral:

---

### Post by Dylan1473 on 2012-08-04
Oh! Well, there isn't a graphical interface to remove those either that I know of but you can find instructions in a few places. It's generally done by removing packages from the terminal. You just need to enter some commands - which desktop environments are you trying to get rid of? A cursory search reveals _[this guide]("http://www.psychocats.net/ubuntu/purexubuntuhttp://")_ for removing all but XFCE. It likely covers some of what you want to do but I'm not sure exactly which ones you're trying to get rid of. Why don't you post the full list of what you want gone so it's possible to provide more precise instructions?

---

### Post by tecknomage on 2012-08-04
To make it clear...

 **I want to remove some of the desktop options (*upper-right icon*) at the Ubuntu login.**

Just remove what is displayed/offered, NOT remove the desktop environments.

Other distributions  of Linux (*example openSUSE, YasT*) have a manager to do this. You just unchecked what environments you did not want offered in the Environment Menu.

---

### Post by Dylan1473 on 2012-08-04
I think that you may be using a login manager that is neither the one I'm using nor the default. I know of no way to do what you are describing in any case - removing the option to login to certain desktop environments without removing the environments themselves? Sorry.

---

