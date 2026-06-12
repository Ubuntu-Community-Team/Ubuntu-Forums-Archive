---
title: "HP Printer networked through Windows"
date: 2010-11-25
forum: General Help
---

### Post by easy_target on 2010-11-25
Okay, I am at a loss.
I have a HP LaserJet 1212nf Multifunction printer connected to a Windows 7 machine. I tried installing it through System>Administration>Printing and when trying to finish the process I am asked for a username and password. I tried everything from local, cups, samba users and passwords and nothing worked.
Tried a different venue through CUPS web interface. Managed to install the printer, but when trying to print a test page, a message pops up saying that I need HP's plugin. Running hp-setup and hp-toolbox the printer cannot be found.(????)
Uninstalled the printer from the CUPS web interface and tried to install it through hp-setup as networking printer. It can't be found either. What is going on? It used to be very straightforward to install printers and share them in older versions of ubuntu but now such a trivial, CRUCIAL task is impossible to perform. For the first time in 6 years of using ubuntu I am considering going back to windows. :confused:
Any help?

---

### Post by deanjm1963 on 2010-11-25
Your printer is supported - [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html") - are you networking the printer or is it connected directly?

I also have a laserjet that needs the plug-in. If it's connected directly, reboot your machine, you should get a pop-up saying that your printer needs a plug-in. Enter your password, a terminal should pop-up and a download should take place. Once that's installed it should work.

Hope this helps.

---

### Post by easy_target on 2010-11-25
The printer is networked and is installed on a Windows 7 machine. If installed directly there are no problems. But my family refuses to use the ubuntu computer, and the printer has to be connected to the windows box. Unfortunately this way I cannot access the printer. Any other ideas?

---

### Post by easy_target on 2010-11-25
Well I guess I am out of luck. Reading the link above:

> Network support indicates built-in ethernet and/or wireless networking. Alternatively, many devices may be operated on the network using an external JetDirect print server. _Not all network configurations are supported._ Please refer to the HPLIP FAQs for more information.

Sooo... I have to WAIT for it to be implemented/supported. Seriously, partial support for network printing? If I were running a business with ubuntu, at this point I would have rushed back to Windows.
I believe that this ends this thread since I got my answer.

---

