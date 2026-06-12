---
title: "LightDM on 11.04"
date: 2011-09-27
forum: General Help
---

### Post by galacticaboy on 2011-09-27
I am trying to install LightDM on Ubuntu 11.04. 
I did this "sudo apt-add-repository ppa:lightdm-team/ppa" and "sudo apt-get install lightdm lightdm-greeter-example-gtk"

When I run "lightdm --test-mode" to test it, it takes me to what looks like a recovery console where I login and enter my password and have to type "sudo stop lightdm" "sudo start gdm" to get back to my desktop. It does not work. What did I do wrong?

---

### Post by Krytarik on 2011-09-27
According to this guide, the "test-mode" feature needs the package "xserver-xephyr" to be installed:

[http://mygeekopinions.blogspot.com/2011/08/how-to-install-lightdm-in-ubuntu-1104.html](http://mygeekopinions.blogspot.com/2011/08/how-to-install-lightdm-in-ubuntu-1104.html)

Otherwise, just choose "lightdm" as the display manager in the dialog that comes up when running this command:
```
sudo dpkg-reconfigure lightdm
```You can run the same command to change it back to "gdm", if needed/wanted. If, after choosing LightDM, you don't even get to a console, boot into "recovery mode" to switch back (you may need to press the Shift key to make the Grub2 boot menu appear).

Hope it works!

---

### Post by galacticaboy on 2011-09-27
This is what my LightDM looks like. I want it to look like the one for 11.10. I think its called Unity Greeter Theme, but I cannot figure out how to do that.

---

### Post by Krytarik on 2011-09-27
> **galacticaboy said:**
> I want it to look like the one for 11.10. I think its called Unity Greeter Theme, but I cannot figure out how to do that.
Well, you could try to extract the content of the package "unity-greeter" of Oneiric 11.10, but it's more than likely that it fails to run because of missing dependencies:

[http://packages.ubuntu.com/oneiric/unity-greeter](http://packages.ubuntu.com/oneiric/unity-greeter)

Therefore, open the deb-package with "Archive Manager" (or "file-roller").

Good luck!

---

