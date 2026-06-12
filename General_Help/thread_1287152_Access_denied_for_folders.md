---
title: "Access denied for folders"
date: 2009-10-09
forum: General Help
---

### Post by AfterShockPivot on 2009-10-09
I'm trying to create a folder in /usr/share/icons/Humanity but Ubuntu is fading out the options to create a folder and copy or paste. How do I get it to allow me permission?

---

### Post by jflaker on 2009-10-09
> **AfterShockPivot said:**
> I'm trying to create a folder in /usr/share/icons/Humanity but Ubuntu is fading out the options to create a folder and copy or paste. How do I get it to allow me permission?

the /usr folder is owned by root and can only be modified (includes creating subfolders, by root.  

you can do from a terminal "sudo nautilus" (without the quotes) and get full permission to that folder and ALL folders for that matter.

If you do this, use EXTREME CAUTION as you not only have the ability to create folder and files in restricted folders, but you can delete stuff too.  DO SO AT YOUR OWN RISK.

May I ask why you want to create a folder under /usr

---

### Post by AfterShockPivot on 2009-10-09
I'm experimenting with themes right now. So hopefully I'll only ruin visual things. Instead of the unix.

---

### Post by jflaker on 2009-10-09
why don't you load up VirtualBox, install Ubuntu in a VirtualMachine and save your workstation from ooops's?

---

### Post by AfterShockPivot on 2009-10-09
What's virtual box?

---

### Post by jflaker on 2009-10-09
This is basically a computer within YOUR computer...

You can create a virtual disk (is really a file under /home/YourID/.virtualbox then install an OS of your choice.  If you mess it up, just delete and reinstall and you current installation, the one you are using now, remains unaffected/intact.

install it through Synaptic Package Manager, it is called "virtualbox-ose"

[http://www.virtualbox.org](http://www.virtualbox.org)
learn more, but install from the package manager....

If anyone else can shed more of an explanation light on VBox, I would appreciate it.

---

### Post by AfterShockPivot on 2009-10-10
what's ooop's?

---

### Post by ad_267 on 2009-10-10
You can edit themes in your home directory (~/.icons and ~/.themes) instead of changing the system wide themes. If you want to change an existing theme you can copy it from the system wide directory and rename it.

---

### Post by jflaker on 2009-10-18
> **AfterShockPivot said:**
> what's ooop's?

a mistake that can take down your system....

---

### Post by andrius7 on 2009-11-10
*hi could anyone help how to access restricted folders and files on ubuntu. Atm i boot from CD but cont access some important files ig ffx boookmarks. I want to access them be4 installing ubuntu on mar HD, pls help *

---

