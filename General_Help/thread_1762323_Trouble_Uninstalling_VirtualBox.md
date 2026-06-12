---
title: "Trouble Uninstalling VirtualBox"
date: 2011-05-19
forum: General Help
---

### Post by jezzyjez on 2011-05-19
I am running 11.04 and am trying to update my vbox. I have been told by synaptic to remove previous version. I located vbox.cfg:

# VirtualBox installation directory
INSTALL_DIR='/opt/VirtualBox'
# VirtualBox version
INSTALL_VER='4.0.0'
INSTALL_REV='69151'

Then moved to the install_dir, I tried to run uninstal.sh however it did nothing. When run in terminal the window opened and closed without displaying any code.

What is the best way to get rid of it?

I'm assuming just deleting the folder is a bad way of doing things

Thanks
Jez

---

### Post by jezzyjez on 2011-05-19
Update, when running uninstal.sh from terminal the error


uninstall.sh: 22: cannot create /var/log/vbox-uninstall.log: Permission denied
cat: /var/log/vbox-uninstall.log: No such file or directory
Error creating log file!  Aborting...


Appears

---

### Post by wildmanne39 on 2011-05-19
> **jezzyjez said:**
> I am running 11.04 and am trying to update my vbox. I have been told by synaptic to remove previous version. I located vbox.cfg:

# VirtualBox installation directory
INSTALL_DIR='/opt/VirtualBox'
# VirtualBox version
INSTALL_VER='4.0.0'
INSTALL_REV='69151'

Then moved to the install_dir, I tried to run uninstal.sh however it did nothing. When run in terminal the window opened and closed without displaying any code.

What is the best way to get rid of it?

I'm assuming just deleting the folder is a bad way of doing things

Thanks
Jez
HI, just use synaptic to remove it.

---

### Post by jezzyjez on 2011-05-19
It does not appear in synaptic as installed. Then when I selected it for installation it gets part way through and says I need to uninstall it first.

---

### Post by wsamh on 2011-05-19
How did you install it orginally?

---

### Post by jezzyjez on 2011-05-19
> **wsamh said:**
> How did you install it orginally?

Not 100% sure but I'm pretty certain it was a .deb file from their website.

However I did this before upgrading form 10.10 to 11.04

Program worked fine before upgrade

---

### Post by wildmanne39 on 2011-05-19
> **jezzyjez said:**
> Not 100% sure but I'm pretty certain it was a .deb file from their website.

However I did this before upgrading form 10.10 to 11.04

Program worked fine before upgrade
Hi, there is a new release for natty, it sounds like you do not have the dkms package installed that rebuilds the kernel, when there is an update to the kernel.

---

### Post by jezzyjez on 2011-05-20
Ok, how do i resolve this?

I've tried installing the new release of the website but it says I need to remove the old one first

---

### Post by linuxinstalledfromhdd on 2011-05-20
You need to open synaptic package manager. And remove it.

Then remove the PPA you installed it with (if applicable) 

Then install Ubuntu Tweak, and run a cache and configuration cleaner. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Then 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean all
sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by SecretCode on 2011-05-20
> **jezzyjez said:**
> Update, when running uninstal.sh from terminal the error


uninstall.sh: 22: cannot create /var/log/vbox-uninstall.log: Permission denied
cat: /var/log/vbox-uninstall.log: No such file or directory
Error creating log file!  Aborting...


Appears

Are you running _**sudo** uninstal.sh _?

---

### Post by wsamh on 2011-05-20
He can't remove from synaptic if it is not showing that it is installed. You should be able to remove it through the terminal. Try 'sudo apt-get remove virtualbox-4.0.0' in the terminal. Hoping that is the right version to tupe in. It does not work. Try replacing '4.0.0' with just '4.0'. 

~Sam

---

