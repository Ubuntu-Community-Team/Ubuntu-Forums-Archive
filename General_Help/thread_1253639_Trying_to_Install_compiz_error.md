---
title: "Trying to Install compiz error"
date: 2009-08-30
forum: General Help
---

### Post by darksniper404 on 2009-08-30
Hi I'm trying to install compiz using this tutorial [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) but on the step that tells me to type in

sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

in the terminal

I get back this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-backend-gconf: Conflicts: libcompizconfig-backend-gconf but 0.6.0~git20071003+3v1ubuntu0 is to be installed
E: Broken packages

Please help.

---

### Post by Liolikas on 2009-08-30
Try simplify things into:
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra

Maybe you do not need that last thing at all?

---

### Post by scouser73 on 2009-08-30
Go to **Terminal** then copy & paste this command: **sudo aptitude install compizconfig-settings-manager**

Then you can find CompizConfig in **System** > **Preferences**

---

### Post by darksniper404 on 2009-08-30
> **Liolikas said:**
> Try simplify things into:
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra

Maybe you do not need that last thing at all?
Thanks that worked now how can I use the cube effect with multiple desktops.

---

### Post by scouser73 on 2009-08-30
Use this tutorial for getting the cube working: [[COLOR="Red"]**CompizConfig Cube Tutorial**[/COLOR]]("http://www.ghacks.net/2009/07/30/configuring-the-appearance-of-the-compiz-cube")

---

### Post by darksniper404 on 2009-08-30
> **scouser73 said:**
> Use this tutorial for getting the cube working: [[COLOR=Red]**CompsizConfig Cube Tutorial**[/COLOR]]("http://www.ghacks.net/2009/07/30/configuring-the-appearance-of-the-compiz-cube")
Thanks I have working now and its awesome I'm so glad I switched to ubuntu.

---

### Post by scouser73 on 2009-08-30
Glad you're liking it mate, it's an awesome O/S, and with Compiz Fusion working, it's just jaw droppingly gorgeous.

---

### Post by darksniper404 on 2009-08-30
> **scouser73 said:**
> Glad you're liking it mate, it's an awesome O/S, and with Compiz Fusion working, it's just jaw droppingly gorgeous.
I logged out and back in and now when I hold ctrl + alt and move my mouse it doesn't work.

---

### Post by darksniper404 on 2009-08-30
It was screwing up my desktop so I reinstalled it and it still will not let me use the cube.

---

### Post by darksniper404 on 2009-08-30
Bump

---

